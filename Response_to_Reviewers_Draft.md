# Response to Reviewers Draft

Manuscript title: **Layout-Aware Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives**

We sincerely thank the reviewer for the detailed and constructive comments. We agree that the original manuscript was too concise and that the experimental evidence needed to be strengthened. In the revised version, we have substantially expanded the method description, added more baselines and evaluation metrics, included statistical uncertainty analysis, added ablation studies, and clarified the scope of the work as page-level layout analysis rather than transcription-based OCR evaluation.

---

## Comment 1: The technical contribution is thin and appears to be only YOLOv8n plus simple sorting.

**Response:** We agree that the original manuscript did not sufficiently explain the full pipeline and its design choices. We have revised the manuscript to clarify that the current contribution is not a new detector architecture, but a reproducible page-level layout-analysis framework for traditional Mongolian historical archives under a realistic no-transcription setting. Specifically, we added:

- a complete pipeline overview figure;
- expanded descriptions of Sauvola-projection, connected-components, rule-based extraction, YOLOv8n detection, and rotation-aware reading-order recovery;
- a more explicit statement that YOLOv8n is used as a lightweight learning-based detector baseline rather than claimed as an architectural novelty;
- an ablation showing that rotation-aware ordering improves reading-order accuracy from 0.820 to 0.920.

We also explicitly acknowledge in the Discussion that stronger detector baselines and architecture-level innovations remain future work.

---

## Comment 2: The dataset is small and the 11-page test split may not support stable conclusions.

**Response:** We agree. To avoid overstating the result, we added page-level bootstrap uncertainty analysis with 1000 resamples on the 11-page test split. The revised manuscript now reports 95% confidence intervals for precision, recall, and F1. For example, the YOLOv8n F1 95% CI is [0.601, 0.866]. We also explicitly state that the current dataset should be interpreted as a low-resource pilot benchmark and that larger-scale annotation is needed for stronger generalization claims.

---

## Comment 3: Only IoU@0.5 is reported; stricter localization metrics and AP are missing.

**Response:** We have added supplementary strict-localization evaluation at IoU@0.75. We also added an approximate project-level AP analysis by sweeping the YOLO confidence threshold and applying 101-point interpolation. The revised manuscript now reports:

- AP@0.50 = 0.810;
- AP@0.75 = 0.321;
- YOLOv8n F1@0.75 = 0.453.

These results show that boundary-accurate localization remains challenging, especially under stricter overlap criteria.

---

## Comment 4: Comparison methods are insufficient.

**Response:** We have expanded the main comparison table from two methods to four methods:

- Sauvola + projection;
- Connected components;
- Rule proposed;
- YOLOv8n + rotation-aware order.

The revised table shows that YOLOv8n outperforms the classical baselines and the stronger rule-based pipeline under the unified IoU@0.5 protocol. We acknowledge that additional strong baselines such as Faster R-CNN, DETR-style detectors, LayoutParser transfer, and DocLayout-YOLO remain important future additions.

---

## Comment 5: Ablation experiments are missing.

**Response:** We added three ablation/sensitivity analyses:

1. **Rotation-aware ordering:** removing it reduces reading-order accuracy from 0.920 to 0.820.
2. **Ignore-region filtering:** removing it increases false positives from 9 to 12 and reduces F1 from 0.745 to 0.736.
3. **Inference-size sensitivity:** using the same YOLOv8n checkpoint, imgsz=960 provides the best F1-speed balance compared with imgsz=640 and 1280.

We clearly mark the image-size study as inference-only, not a retraining ablation.

---

## Comment 6: The paper lacks a pipeline figure and annotation examples.

**Response:** We added two new figures:

- a page-level layout-analysis pipeline overview;
- an annotation example showing valid text columns, ignore regions, and reading-order labels.

We also retained the qualitative GT / rule-based / YOLO comparison figure.

---

## Comment 7: Annotation quality and IAA are not reported.

**Response:** We agree that inter-annotator agreement is important. The current revision now describes the annotation protocol more clearly and explicitly lists IAA as a limitation. Since a second independent annotator is not yet available, we do not fabricate an IAA result. We plan to add a 5--10 page double-annotation subset in the next experimental round.

---

## Comment 8: Runtime and deployment analysis are missing.

**Response:** We added local CPU runtime analysis on the 11-page test split. YOLOv8n requires 0.193 seconds per page on average, compared with 1.843 seconds per page for the rule-based pipeline. This result suggests that the learning-based detector is both more accurate and faster in the current implementation.

---

## Comment 9: The manuscript should not claim OCR accuracy without expert transcripts.

**Response:** We fully agree. The revised manuscript consistently states that CER/WER is not reported because expert column-level transcripts are unavailable. We use the term “recognition-ready pipeline” only to describe the export of oracle and detected column crops for future OCR evaluation. We do not claim end-to-end OCR accuracy.

---

## Remaining limitations acknowledged in the revised manuscript

The revised manuscript now explicitly acknowledges the following limitations:

- small test split and wide bootstrap intervals;
- lack of expert transcription and therefore no CER/WER;
- no IAA yet;
- no strong detector baselines such as Faster R-CNN / DETR / DocLayout-YOLO yet;
- inference-size sensitivity is not equivalent to full retraining ablation;
- boundary localization remains challenging under IoU@0.75.

---

## Additional update: Strong detector baseline

Following the reviewer’s concern about insufficient comparison methods, we added a COCO-pretrained Faster R-CNN MobileNetV3-FPN baseline. The detector is fine-tuned for 5 epochs, and its confidence threshold is selected on the validation split. On the test split, this baseline achieves P=0.917, R=0.681, F1=0.782, mean IoU=0.738, and reading-order accuracy=0.860. This provides a stronger two-stage detector comparison and shows that learning-based detectors consistently outperform the rule-based baseline.
