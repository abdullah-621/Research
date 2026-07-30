# Dataset Preparation and Splitting Summary

## Overview

The dataset was prepared and split using a custom preprocessing notebook designed to ensure a clean and reliable experimental setup for deep learning model training and evaluation. The primary objectives of the preprocessing pipeline were:

* Remove duplicate images
* Preserve class distribution across all splits
* Create independent training, validation, and testing subsets
* Prevent data leakage between dataset partitions

## Original Dataset Statistics

The original dataset contained **4,610 unique images** distributed across **15 classes** representing diseases and healthy conditions of jute, tea, and wheat plants.

| Category                  | Number of Images |
| ------------------------- | ---------------: |
| Total images              |        **4,610** |
| Total classes             |           **15** |
| Duplicate images detected |            **0** |

Since no duplicate images were found during the preprocessing stage, all **4,610 images** were retained for the final dataset.

## Class Distribution

| Class                           | Images |
| ------------------------------- | -----: |
| Jute_Data__Cescospora_Leaf_Spot |     94 |
| Jute_Data__Golden_Mosaic        |    347 |
| Jute_Data__Healthy_Leaf         |    201 |
| Tea_Data__Algal_leaf_spot       |    350 |
| Tea_Data__Brown_Blight          |    350 |
| Tea_Data__Gray_Blight           |    350 |
| Tea_Data__Healthy               |    350 |
| Tea_Data__Helopelties           |    350 |
| Tea_Data__Red_Rust              |    350 |
| Tea_Data__Red_Spider            |    400 |
| Wheat_Data__BlackPoint          |    303 |
| Wheat_Data__FusariumFootRot     |    248 |
| Wheat_Data__HealthyLeaf         |    250 |
| Wheat_Data__LeafBlight          |    362 |
| Wheat_Data__WheatBlast          |    305 |

## Dataset Splitting Strategy

A **stratified train-validation-test split** was performed to preserve the proportion of each class across all subsets.

The dataset was divided using the following ratio:

* **Training set:** 70%
* **Testing set:** 20%
* **Validation set:** 10%

### Final Split

| Split      |    Images | Percentage |
| ---------- | --------: | ---------: |
| Train      | **3,226** |        70% |
| Test       |   **922** |        20% |
| Validation |   **462** |        10% |
| **Total**  | **4,610** |   **100%** |

## Final Class Distribution After Splitting

| Class                           | Train | Test | Validation |
| ------------------------------- | ----: | ---: | ---------: |
| Jute_Data__Cescospora_Leaf_Spot |    66 |   19 |          9 |
| Jute_Data__Golden_Mosaic        |   243 |   69 |         35 |
| Jute_Data__Healthy_Leaf         |   141 |   40 |         20 |
| Tea_Data__Algal_leaf_spot       |   245 |   70 |         35 |
| Tea_Data__Brown_Blight          |   245 |   70 |         35 |
| Tea_Data__Gray_Blight           |   245 |   70 |         35 |
| Tea_Data__Healthy               |   245 |   70 |         35 |
| Tea_Data__Helopelties           |   245 |   70 |         35 |
| Tea_Data__Red_Rust              |   245 |   70 |         35 |
| Tea_Data__Red_Spider            |   280 |   80 |         40 |
| Wheat_Data__BlackPoint          |   212 |   61 |         30 |
| Wheat_Data__FusariumFootRot     |   173 |   50 |         25 |
| Wheat_Data__HealthyLeaf         |   175 |   50 |         25 |
| Wheat_Data__LeafBlight          |   253 |   72 |         37 |
| Wheat_Data__WheatBlast          |   213 |   61 |         31 |

## Data Integrity Verification

To ensure that no image appeared in more than one subset, a hash-based duplicate verification was performed across all partitions.

### Cross-Split Duplicate Check

| Comparison          | Duplicate Images |
| ------------------- | ---------------: |
| Train vs Test       |                0 |
| Train vs Validation |                0 |
| Test vs Validation  |                0 |

This confirms that the dataset partitions are **mutually exclusive**, eliminating the possibility of data leakage during model training and evaluation.

## Output Dataset Structure

The processed dataset was organized into a standard Keras-compatible directory structure:

```text
Split_Dataset/
├── train/
├── test/
└── val/
```

Each subset contains separate folders for all 15 classes, allowing direct use with `image_dataset_from_directory()` or other deep learning data loaders.

## Summary

The preprocessing pipeline produced a **clean, balanced, and leakage-free dataset** consisting of **4,610 unique images** across **15 classes**. The data was stratified and split into **3,226 training**, **922 testing**, and **462 validation** images while preserving class distribution and ensuring that **no duplicate image exists across the train, validation, and test sets**. This dataset configuration is suitable for training, validating, and benchmarking deep learning models under a reliable experimental protocol.
