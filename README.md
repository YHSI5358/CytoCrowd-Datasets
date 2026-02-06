# CytoCrowd: A Multi-Annotator Benchmark Dataset for Cytology Image Analysis

**Status:** Accepted for publication at WWW '26 (Proceedings of the ACM Web Conference 2026).
**Note:** This repository provides the dataset documentation and specifications to support the review process of related works.

---

## 1. Overview
**CytoCrowd** is a new public benchmark designed to bridge the gap between crowdsourcing annotation aggregation and medical image analysis. Unlike existing datasets that either offer a single consensus ground truth (masking expert disagreement) or raw multi-annotator labels without a gold standard, CytoCrowd provides **both**:
1.  **Raw, conflicting annotations** from four independent board-certified pathologists.
2.  **A high-quality gold-standard ground truth** rigorously verified by a senior expert (15+ years of experience).

This dual structure makes CytoCrowd a versatile resource for evaluating **Annotation Aggregation** algorithms (resolving conflicts) and training robust **Computer Vision** models.

## 2. Key Features
*   **Domain:** Cytology Image Analysis (Whole-slide scanner at 40x magnification).
*   **Image Resolution:** High-resolution patches containing dense, overlapping cellular objects.
*   **Expert Annotation:** All annotators are board-certified pathologists with clinical experience.
*   **Real-world Disagreement:** Captures significant inter-observer variability in object boundaries, categories, and object existence.

## 3. Dataset Statistics
The dataset was constructed over a seven-month collaborative project involving medical institutions and research labs.

| Statistic | Value | Description |
| :--- | :--- | :--- |
| **# Images (Tasks)** | **446** | High-resolution cytology images. |
| **# Annotators** | **4** | Independent pathologists (Workers). |
| **# Raw Annotations** | **14,579** | Total bounding boxes drawn by the 4 workers. |
| **# Ground Truth Objects** | **6,402** | Final objects verified by the senior expert. |
| **# Categories** | **34** | Fine-grained diagnostic categories. |
| **Avg. Pairwise IoU** | **0.664** | Indicates significant localized disagreement. |

### Disagreement Analysis
*   **Existence Conflict:** Only **11.37%** of cells were identified by all four experts simultaneously, while **34.78%** were annotated by only a single expert.
*   **Ratio:** The ratio of raw annotations to ground truth objects is approx **2.28 to 1**, highlighting the noise and redundancy in raw expert labels.

## 4. Dataset Construction & Quality Control
The construction process ensures the highest quality for benchmarking:
1.  **Independent Annotation:** Four pathologists annotated images blindly using a custom platform to ensure independence.
2.  **Gold Standard Verification:** A senior pathologist reviewed **every one of the 14,579 raw annotations**. They consolidated, corrected, and finalized the ROIs and categories to establish the definitive ground truth.


## 5. Supported Tasks
CytoCrowd supports two primary research directions:

### Task 1: Medical Object Detection (CV)
*   **Goal:** Train models to identify cell locations and categories.
*   **Ground Truth:** Uses the Senior Expert's gold standard.
*   **Challenge:** Handling fine-grained categories and dense object overlaps.

### Task 2: Annotation Aggregation (Crowdsourcing)
*   **Goal:** Input the noisy, conflicting annotations from the 4 workers and output a single aggregated label.
*   **Evaluation:** The aggregated result is compared against the Senior Expert's ground truth.
*   **Challenge:** Resolving high-level disagreements on object existence and class ambiguity without access to the ground truth during inference.

## 8. Citation
If you use this dataset, please cite the paper (Publication details to be updated upon proceedings release):

> **CytoCrowd: A Multi-Annotator Benchmark Dataset for Cytology Image Analysis.**
> *In Proceedings of the ACM Web Conference 2026 (WWW '26).*

---
*For reviewing purposes, the full anonymous definition paper is available in this repository as `CytoCrowd_Reference_Anonymous.pdf`.*
