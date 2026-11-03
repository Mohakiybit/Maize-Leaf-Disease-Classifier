# Maize leaf disease classifier (Tanzania): leak-aware evaluation

A PyTorch image classifier for three maize leaf classes: **healthy**, **Maize Lethal Necrosis (MLN)** and **Maize Streak Virus (MSV)**, built with transfer learning on the Tanzanian maize imagery dataset.

The emphasis of this project is an honest evaluation. Before training, the data was checked for near-duplicate photos, the train/validation/test split was built so that look-alike images never end up on both sides, and the test set was run exactly once.

> **Status: in progress.** Done: data audit, near-duplicate analysis, leak-aware split, frozen-backbone baseline, fine-tuning, one-time test evaluation. Grad-CAM heatmaps have been generated (notebook 08); the written findings are still to come, along with a test on images from another source, a Gradio demo, and a final write-up.

## Results so far

| Model | Validation accuracy | Test accuracy (845 images, 95% range) | Parameters | File size | CPU time per image |
|---|---|---|---|---|---|
| ResNet18, frozen backbone (baseline) | 91.3% | not run on test | | | |
| ResNet18, last block fine-tuned | 97.3% | not run on test | 11.2M | 45 MB | 56 ms |
| ResNet18, last two blocks fine-tuned | 98.1% | **97.9%** (96.7 to 98.6) | 11.2M | 45 MB | 58 ms |
| MobileNetV2, last six blocks fine-tuned | 97.5% | **96.8%** (95.4 to 97.8) | 2.2M | 9 MB | 24 ms |

- Fine-tuning improved on the frozen baseline: ResNet18 by 6 to 7 points of validation accuracy (91.3% to 97.3% and 98.1%), and MobileNetV2 from 85.3% with a frozen backbone to 97.5%. Each gain is significant on a paired McNemar test over the same 850 validation images (p < 0.001).
- MobileNetV2 was declared the primary model **before** the test set was run. On the test set, ResNet18 (last two blocks) got 16 images right that MobileNetV2 missed, and MobileNetV2 got 7 right that ResNet18 missed (McNemar p = 0.093): a difference of about one point that is not statistically established. MobileNetV2 is about 5 times smaller and 2.4 times faster on CPU.
- MobileNetV2 on the test set: per-class recall / precision were HEALTHY 0.992 / 0.980, MLN 0.958 / 0.971, MSV 0.958 / 0.954. It caught 592 of 597 diseased leaves (99.2%) and flagged 2 of 248 healthy leaves as diseased. Of its 27 mistakes, 20 were MLN confused with MSV.
- Test accuracy came out 0.3 to 0.7 points below validation, as expected: validation was used to pick the best epoch and model.

Raw logged output from each run is in [`results/`](results/).

## What was checked, and why

1. **Data audit.** 9,356 images (HEALTHY 3,073; MLN 3,231; MSV 3,052), mostly 1536x2048 or 2048x1536 JPEGs. No metadata files and no GPS tags, so splitting by farm or plant is not possible. No byte-identical duplicates.
2. **Near-duplicate analysis.** Each image was embedded with an ImageNet ResNet18 and all pairs compared. At a cosine similarity of 0.85 or higher there are 8,222 pairs, and 31% of images belong to a cluster of look-alikes. A plain random 80/10/10 split would be expected to put a near-duplicate of about 28% of test images into the training set. Cross-class look-alike pairs were inspected by eye: they were different photos with similar leaf texture, not mislabelled copies.
3. **Leak-aware split.** Whole clusters were kept together (stratified by class). Validation and test images that still had a look-alike (similarity 0.85 or higher) in training were then dropped: 176 images (1.9%). Result: 7,485 train / 850 validation / 845 test, with no flagged pair crossing a split boundary.
4. **Training.** Frozen-backbone baseline, then fine-tuning with a small learning rate for the unfrozen layers, all judged on the validation set. The model's ability to learn was confirmed first by overfitting 32 images.
5. **One test run.** The test set was evaluated once, with the primary model declared first, and a lock file preventing a second run.

## Limitations

- There are no farm, plant or session identifiers, so look-alike detection relies on image similarity alone. Photos of the same leaf from a different angle may still sit on both sides of a split.
- Cross-class mistakes are concentrated between MLN and MSV, which look alike.
- All images come from a single collection. Accuracy on photos from other sources has not been measured yet; expect it to be lower.
- Validation was used to pick epochs and models, so validation numbers are slightly optimistic; cite the test numbers. Each model was trained with a single random seed, and differences of about one point between models are within noise.
- Dropping the validation/test images most similar to training images probably makes those sets a little harder than a random split would.
- This is a pilot model trained on Tanzanian data. It is not a diagnostic tool.

## Reproducing

The notebooks are written for Google Colab (a T4 GPU for notebooks 04 to 08) and are meant to be run in order. They read the previous step's output from Colab and Google Drive (`/content/...` and `MyDrive/maize_ckpt`). The notebooks in this repository have no saved outputs; the logged outputs from the actual runs are in `results/`.

| Notebook | Purpose |
|---|---|
| `01_data_audit` | Class counts, image sizes, metadata, exact and perceptual-hash duplicates |
| `02_duplicate_analysis` | Embedding-based near-duplicate pairs and clusters, leakage estimate |
| `03_leak_aware_split` | Cluster split, purge, resized train/val/test folders |
| `04_loaders_and_overfit_test` | Augmentation, batch inspection, 32-image overfit test |
| `05_frozen_baseline` | Frozen ResNet18 baseline |
| `06_finetuning` | Fine-tuning experiments and paired tests |
| `07_test_evaluation` | One-time test evaluation with lock file |
| `08_gradcam` | Grad-CAM heatmaps of correct and wrong predictions, plus a deletion test of how faithful they are |

## Data

The dataset is **not** included here. Download it from Mendeley Data: *Maize Imagery Dataset - Tanzania*, Version 1, published 22 February 2023, DOI [10.17632/fkw49mz3xs.1](https://doi.org/10.17632/fkw49mz3xs.1), Nelson Mandela African Institute of Science and Technology. Please check the licence and the author list on the dataset page and cite them if you reuse the data.
