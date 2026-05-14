# Pre-submission Response-to-Reviewers Draft

Manuscript title: **Layout-Aware Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives**

This document summarizes major concerns identified during internal review and the corresponding revisions already made before submission.

---

## 1. Concern: Dataset size is small.

**Response:** We agree. The manuscript has been reframed as a **pilot-scale low-resource benchmark** rather than a large-scale benchmark or complete OCR system. We expanded the dataset from 62 to 105 pages (43 train + 8 val + 54 test) by merging annotation Project 15 and Project 16. The main results now use the expanded 54-page test set (786 valid text-column ground-truth boxes). The original 11-page test is retained for diagnostic tables with explicit labeling. We also added dataset distribution statistics.

**Revision made:** Expanded dataset to 105 pages; added Table `dataset_distribution`; updated all main results to 54-page test set; updated bootstrap CIs; all original 11-page tables labeled as diagnostic.

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

**Response:** We added a training-budget and threshold-selection protocol table documenting all models' epochs and threshold sources. We further conducted fair-budget (50-epoch) retraining of RT-DETR-L and DocLayout-YOLO to match YOLOv8n's training budget (previously they were trained for only 5 epochs). The results are informative: DocLayout-YOLO improved from F1 = 0.037 (5ep) to F1 = 0.602 (50ep), a 16$\times$ improvement, though still below YOLOv8n (0.820). RT-DETR improved from 0.058 to 0.153. The transfer baselines table now reports both budgets. This directly addresses the concern by showing that while fair-budget training substantially improves transfer performance, the domain gap remains the primary bottleneck. We also discuss that Faster R-CNN was trained for only 5 epochs and a compute-matched comparison is left to future work.

**Revision made:** Updated `training_protocol` table with 50ep rows; updated `transfer_baselines` table with dual-budget results; revised discussion to emphasize fair-budget comparison.

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

- 105 total pages with 54 test pages (adequate for a pilot study but modest by modern CV standards);
- 5-page IAA subset (sufficient for minimum diagnostic, but 10--15 pages would be more informative);
- no completed expert OCR transcript set yet (crop package prepared, awaiting expert availability);
- low full-page success rate (0.074 for YOLOv8n on the expanded test);
- Faster R-CNN trained for only 5 epochs (needs compute-matched optimization);
- transfer baselines improved substantially with fair-budget training but still underperform;
- limited algorithmic novelty compared with a full method paper.

These limitations are now stated directly in the manuscript.

---

## Second-Round Revision (R2) — 2026-05-14

### Critical fix
- **Threshold table caption**: Corrected "11-page validation split" to "8-page validation split" (the dataset has 8 validation pages, not 11).

### Minor improvements
- **Conclusion wording**: Changed "outperforms" to "achieves higher F1 than ... under the reported protocol" to reduce competition-style language.
- **Transfer baseline footnote**: Added explicit statement that transfer baselines are evaluated on 11-page test rather than expanded 54-page test due to computational resource limits, with expanded evaluation planned for future work.
- **Related Work**: Added 3 references — dhSegment (Oliveira et al., ICFHR 2018), DIVA-HisDB (Simistira et al., ICFHR 2016), ICDAR RDCL (Clausner et al., ICDAR 2019) — bringing bibliography to 18 entries.
- **Reference citations**: Integrated new references into Historical Document Layout Analysis subsection.
