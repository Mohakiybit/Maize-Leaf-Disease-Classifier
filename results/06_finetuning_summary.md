# Days 7-8 summary (fine-tuning experiments, validation set only)
- Phase 1 baseline: frozen ResNet18, val accuracy 0.9129 (see Day 5-6 summary)

- r18_layer4 (resnet18, unfrozen: layer4, lr 0.0001/0.0003, 10 epochs): val acc 0.9129 -> 0.9729 (best epoch 8), fixed 60 / broke 9, McNemar p = 0.000; 11.2M params, 45 MB, 56 ms/image CPU; recall HEALTHY 0.996, recall MLN 0.966, recall MSV 0.960; confusion [[252, 1, 0], [2, 308, 9], [1, 10, 267]]
- r18_layer3_4 (resnet18, unfrozen: layer3+layer4, lr 0.0001/0.0003, 10 epochs): val acc 0.9129 -> 0.9812 (best epoch 9), fixed 65 / broke 7, McNemar p = 0.000; 11.2M params, 45 MB, 58 ms/image CPU; recall HEALTHY 1.000, recall MLN 0.978, recall MSV 0.968; confusion [[253, 0, 0], [2, 312, 5], [0, 9, 269]]
- mnv2_last6 (mobilenet_v2, unfrozen: features.13+features.14+features.15+features.16+features.17+features.18, lr 0.0001/0.0003, 10 epochs, 5 head-only epochs first): val acc 0.8529 -> 0.9753 (best epoch 8), fixed 111 / broke 7, McNemar p = 0.000; 2.2M params, 9 MB, 24 ms/image CPU; recall HEALTHY 0.996, recall MLN 0.969, recall MSV 0.964; confusion [[252, 0, 1], [1, 309, 9], [2, 8, 268]]

