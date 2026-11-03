# Day 9 summary (test set, evaluated once)
- primary model (declared before testing): mnv2_last6; evaluated: mnv2_last6, r18_layer3_4
- test images: 845

- mnv2_last6: test accuracy 0.9680 (95% range 0.954 to 0.978); validation was 0.9753
  - recall / precision: HEALTHY 0.992 / 0.980; MLN 0.958 / 0.971; MSV 0.958 / 0.954
  - diseased caught 0.992 (5 diseased called healthy); healthy cleared 0.992 (2 healthy flagged)
  - confusion (rows true, columns predicted, order HEALTHY, MLN, MSV): [[246, 0, 2], [2, 300, 11], [3, 9, 272]]
  - size 9 MB, 2.2M params, 24 ms/image on CPU
- r18_layer3_4: test accuracy 0.9787 (95% range 0.967 to 0.986); validation was 0.9812
  - recall / precision: HEALTHY 1.000 / 0.976; MLN 0.974 / 0.981; MSV 0.965 / 0.979
  - diseased caught 0.990 (6 diseased called healthy); healthy cleared 1.000 (0 healthy flagged)
  - confusion (rows true, columns predicted, order HEALTHY, MLN, MSV): [[248, 0, 0], [2, 305, 6], [4, 6, 274]]
  - size 45 MB, 11.2M params, 58 ms/image on CPU
- paired comparison of the two models on test: 7 vs 16 discordant images, McNemar p = 0.093
- mistakes by the primary model: 27; median confidence on mistakes 0.776 vs correct 1.000
