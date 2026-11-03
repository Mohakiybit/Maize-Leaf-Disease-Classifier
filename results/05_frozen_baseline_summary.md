# Day 5-6 summary (frozen ResNet18 baseline)
- config: epochs 12, Adam lr 0.001 (cosine), batch 64, seed 0; train aug as Day 4; test set NOT used
- best epoch 10: val accuracy 0.9129 (+/- 0.019), val loss 0.2599, train accuracy 0.9189
- last epoch: val accuracy 0.9082, train accuracy 0.9194
- seconds per epoch: about 67
- per-class recall / precision (best epoch): HEALTHY 0.945 / 0.964; MLN 0.890 / 0.913; MSV 0.910 / 0.869
- confusion matrix (rows true, columns predicted, order HEALTHY, MLN, MSV): [[239, 7, 7], [4, 284, 31], [5, 20, 253]]
- checkpoint: /content/drive/MyDrive/maize_ckpt/phase1_frozen_resnet18_best.pt
