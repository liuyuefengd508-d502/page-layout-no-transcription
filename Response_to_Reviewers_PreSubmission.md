# Pre-submission Response-to-Reviewers Draft

Manuscript title: **Layout-Aware Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives**

This document summarizes major concerns identified during internal review and the corresponding revisions already made before submission.

---

## 1. Concern: Dataset size is small.

**Response:** We agree. The manuscript has been reframed as a **pilot-scale low-resource benchmark** rather than a large-scale benchmark or complete OCR system. The abstract, contributions, discussion, and conclusion now explicitly state the pilot-scale nature of the dataset. We also added dataset distribution statistics, including page size, column count, Ignore region count, column-box width/height, number of rotated/corrected pages, and pages containing Ignore regions.

**Revision made:** Added Table `dataset_distribution` and pilot-scale wording throughout the manuscript.

---

## 2. Concern: Method innovation is limited.

**Response:** We clarified that the manuscript is primarily a benchmark/protocol paper for an underrepresented archival script setting, not a detector-architecture paper. We expanded the method description and added diagnostic experiments to examine column-aware priors and transfer baselines. The column-aware post-processing experiment is reported honestly: it improves validation F1 but reduces test F1, showing that hand-tuned geometric priors can overfit.

**Revision made:** Added `Column-Aware Post-processing Diagnostic`, transfer-baseline discussion, and stronger benchmark/protocol framing.

---

## 3. Concern: The system should not claim end-to-end OCR ability without transcripts.

**Response:** We fully agree. We replaced “recognition-ready” language with **“crop-export-ready interface”** and explicitly state that CER/WER is not reported because expert column-level transcripts are unavailable. The conclusion states that the current system should be viewed as a **candidate crop generator**, not a fully automatic page-level OCR preprocessing solution.

**Revision made:** Updated abstract, contributions, method, discussion, conclusion, and Data Availability language.

---

## 4. Concern: Full-page success rate is zero.

**Response:** We now report complete detection rate and full-page success rate explicitly. Both are 0 on the current test split. We discuss this as an important limitation and clarify that the current system is not yet fully automatic.

**Revision made:** Added strict page-level metrics and conclusion statement.

---

## 5. Concern: Faster R-CNN outperforms YOLOv8n at IoU@0.5, but the manuscript focused too much on YOLO.

**Response:** We added Faster R-CNN to additional analyses: IoU@0.75, bootstrap confidence intervals, runtime, and approximate AP. The revised text explains that Faster R-CNN has stronger IoU@0.5 F1, whereas YOLOv8n has better strict-boundary AP@0.75.

**Revision made:** Updated strict-localization, bootstrap, runtime, and AP tables.

---

## 6. Concern: Baseline training budgets are not identical.

**Response:** We added a training-budget and threshold-selection protocol table. RT-DETR and DocLayout-YOLO are now explicitly described as **diagnostic transfer experiments**, not fully optimized head-to-head comparisons. We also state that Faster R-CNN was not exhaustively optimized and deserves future compute-matched study.

**Revision made:** Added `training_protocol` table and revised discussion.

---

## 7. Concern: Evaluation metrics are insufficient.

**Response:** The revised manuscript now includes TP/FP/FN counts, IoU@0.75, approximate AP, bootstrap confidence intervals, runtime, complete detection rate, full-page success rate, Kendall’s tau, Spearman’s rho, stratified diagnostic results, and Ignore filtering ablation.

**Revision made:** Added multiple supplementary tables and diagnostic analyses.

---

## 8. Concern: Ignore regions are weakly defined and IAA for Ignore is low.

**Response:** We added English and Chinese annotation guidelines and refined Ignore into recommended subtypes: seal, stain/noise, border/edge, non-target language, ambiguous fragment, and overlap-unseparable. We explicitly acknowledge that Ignore agreement remains a limitation and that more examples and annotator training are needed.

**Revision made:** Added Ignore subtype table and annotation guideline files.

---

## 9. Concern: Downstream OCR value is not verified.

**Response:** We prepared a small OCR case-study package for expert transcription, containing 3 selected pages and 24 oracle text-column crops. We do not report CER/WER until expert transcripts are returned. Scripts are provided to compute oracle-crop and detected-crop CER/WER once transcripts are available.

**Revision made:** Created expert transcription package and evaluation scripts; manuscript remains conservative until true transcripts are available.

---

## Remaining limitations

We acknowledge that the current work remains limited by:

- 62 total pages and 11 test pages;
- 5-page IAA subset;
- no completed expert OCR transcript set yet;
- zero complete full-page success on the current test split;
- no compute-matched detector comparison;
- limited algorithmic novelty compared with a full method paper.

These limitations are now stated directly in the manuscript.
