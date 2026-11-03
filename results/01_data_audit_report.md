# Day 1 audit report

Root: `/content/maize_data`

**Total images: 9356**  |  unreadable: 0

## Class counts

| class | images | share |
|---|---|---|
| Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY | 3073 | 32.8% |
| Maize Imagery Dataset - Tanzania/MLN/MLN | 3231 | 34.5% |
| Maize Imagery Dataset - Tanzania/MSV/MSV | 3052 | 32.6% |

Imbalance ratio (largest/smallest): 1.06

## Image sizes (top 10)

- 1536x2048: 4556
- 2048x1536: 2080
- 1639x1919: 6
- 1874x1678: 6
- 1732x1816: 5
- 1876x1674: 5
- 1778x1770: 5
- 1734x1814: 5
- 1710x1838: 5
- 1711x1837: 5

Distinct sizes: 2235.  Modes: {'RGB': 9356}

## File naming patterns (top 3 per class)

- Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY: `HEALTHY_#` x3070; `HEALTHY_#_#` x3
- Maize Imagery Dataset - Tanzania/MLN/MLN: `MLN_#` x3225; `MLN_#_#` x6
- Maize Imagery Dataset - Tanzania/MSV/MSV: `MSV_#` x3048; `MSV_#_#` x4

## Metadata-like files

None found. Farm/session split is not possible from files alone.

Images with EXIF GPS tag: 0 of 9356

## Duplicates

- Exact duplicate groups: 0 (0 redundant files)
- Exact duplicates spanning different classes (label conflict): 0
- Near-duplicate pairs (dHash distance <= 4): 599
  - d=4: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2670.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_1944.JPEG
  - d=3: Maize Imagery Dataset - Tanzania/MLN/MLN/MLN_83.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2120.JPEG
  - d=3: Maize Imagery Dataset - Tanzania/MLN/MLN/MLN_83.JPEG  <->  Maize Imagery Dataset - Tanzania/MSV/MSV/MSV_1094.JPEG
  - d=2: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2120.JPEG  <->  Maize Imagery Dataset - Tanzania/MSV/MSV/MSV_1094.JPEG
  - d=4: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_489.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_1271.JPEG
  - d=4: Maize Imagery Dataset - Tanzania/MSV/MSV/MSV_673.JPEG  <->  Maize Imagery Dataset - Tanzania/MSV/MSV/MSV_658.JPEG
  - d=4: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_822.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_955.JPEG
  - d=1: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_822.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2487.JPEG
  - d=2: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_822.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_669.JPEG
  - d=3: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_822.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_1210.JPEG
  - d=4: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_955.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2262.JPEG
  - d=3: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2487.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_669.JPEG
  - d=1: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2487.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2262.JPEG
  - d=4: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2487.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_1210.JPEG
  - d=2: Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_669.JPEG  <->  Maize Imagery Dataset - Tanzania/HEALTHY/HEALTHY/HEALTHY_2262.JPEG

