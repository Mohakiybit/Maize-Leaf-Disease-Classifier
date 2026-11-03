# Day 3 summary
- images: 9356; split by cluster (seed 0), then purged at similarity 0.85
- train 7485, val 850, test 845, dropped 176 (1.9%)
- dropped from val: 86 (9.2% of val); from test: 90 (9.6% of test)
- flagged pairs crossing a split after purge: 0
- class counts per split:
  - HEALTHY: train 2459, val 253, test 248, dropped 113
  - MLN: train 2582, val 319, test 313, dropped 17
  - MSV: train 2444, val 278, test 284, dropped 46
