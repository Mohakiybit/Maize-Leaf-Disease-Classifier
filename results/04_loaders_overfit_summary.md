# Day 4 summary
- device: cuda
- classes: {'HEALTHY': 0, 'MLN': 1, 'MSV': 2}
- images: train 7485, val 850, test 845
- augmentation: RandomResizedCrop(224, scale 0.6-1.0), h/v flip, rotation 20, ColorJitter(0.2, 0.2, 0.2, 0.02); eval: resize 256 + centre crop 224
- loading speed: about 88 images/s (~1.4 min/epoch if loading-bound)
- overfit test: first loss 1.029, last loss 0.0000, accuracy 1.00 -> PASSED
