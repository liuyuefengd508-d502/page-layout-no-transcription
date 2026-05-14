Dear Editor,

We submit our manuscript entitled **"A Pilot Study for Text-Column Detection and Reading-Order Evaluation in Traditional Mongolian Historical Archives"** for consideration in the *Journal of King Saud University — Computer and Information Sciences*.

**Context and importance.** Traditional Mongolian historical archives represent a culturally significant yet computationally underexplored document analysis problem. The script is vertically written, cursive, handwritten, and frequently degraded by aging, seals, stains, and scanning artifacts. Page-level layout analysis for these archives has received almost no attention in the document analysis literature, and no expert text transcription is currently available — making standard OCR evaluation impossible. Our work addresses this gap by focusing on the upstream layout tasks that must be solved before any recognition pipeline can operate on these materials.

**What we did.** We constructed a 105-page annotated dataset and compared classical rule-based extraction against YOLOv8n and Faster R-CNN detectors on an expanded 54-page test set. We further conducted fair-budget (50-epoch) retraining of two modern document-layout transfer baselines (RT-DETR-L and DocLayout-YOLO) to test whether off-the-shelf layout priors transfer to this domain. All results are accompanied by bootstrap confidence intervals, strict-localization metrics, stratified subgroup analysis, and inter-annotator agreement diagnostics on a 5-page subset.

**Key findings.** YOLOv8n achieves an F1 of 0.875 compared with 0.722 for the heuristic baseline on the expanded test set. DocLayout-YOLO improves from F1 = 0.037 (5 epochs) to 0.602 (50 epochs), demonstrating that modern layout priors do contain transferable features but require substantial domain adaptation — a finding that would be missed by short-budget comparison alone. However, full-page success remains low (0.074 for YOLOv8n), so the system is positioned as a candidate crop generator and diagnostic evaluation package rather than a fully automatic solution.

**Why JKSU CIS.** The manuscript contributes to computer vision and pattern recognition (document layout detection, evaluation methodology), image processing (historical document preprocessing), and machine learning (transfer learning diagnostics for low-resource domains). At the same time, it addresses a real-world cultural heritage problem with an underrepresented script. We believe this combination of rigorous evaluation, honest limitation disclosure, and cultural significance aligns well with the journal's scope.

**Positioning and disclosure.** The manuscript is explicitly positioned as a pilot/diagnostic study, not as a new detector architecture or a complete OCR system. We do not report CER/WER because expert column-level transcripts are not yet available. All limitations — including a small validation set (8 pages), unequal training budgets for some baselines, low full-page success, and modest inter-annotator agreement on Ignore regions — are stated directly in the manuscript. Non-image research artifacts (annotations, prediction files, evaluation scripts, training protocol documentation) are prepared for release to maximize auditability.

This manuscript is original, has not been published elsewhere, and is not under consideration by another journal. All authors have approved the submission.

Sincerely,

Lanying Liang and Yuefeng Liu
