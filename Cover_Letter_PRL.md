Dear Editor,

We submit our manuscript entitled "Pilot-Scale Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives" for consideration in *Pattern Recognition Letters*.

**What we did.** We constructed a 105-page annotated dataset of traditional Mongolian archival pages and compared heuristic, YOLOv8n, and Faster R-CNN detectors on an expanded 54-page test set. We further conducted fair-budget (50-epoch) retraining of RT-DETR-L and DocLayout-YOLO transfer baselines to test whether modern document-layout priors transfer to this domain. All results are accompanied by bootstrap confidence intervals, stratified analysis, and inter-annotator agreement diagnostics.

**Key findings.** On the expanded test set, YOLOv8n achieves F1 = 0.875 vs. 0.722 for the heuristic baseline. DocLayout-YOLO improves from F1 = 0.037 (5 epochs) to 0.602 (50 epochs), a 16x increase demonstrating that modern layout priors contain transferable features that emerge with sufficient domain adaptation. Full-page success remains low (0.074) and no CER/WER is reported, consistent with the pilot-scale positioning.

**Why PRL.** The manuscript is prepared as a concise communication (10 pages) reporting a pilot-scale evaluation protocol for an underexplored document analysis problem. It fits PRL's scope in pattern recognition and image analysis, while contributing a transparent benchmark for a low-resource cultural heritage script. The work does not propose a new detector architecture; the contribution is the evaluation framework and the diagnostic comparison methodology.

This manuscript has not been published and is not under consideration elsewhere. All authors have approved the submission.

Sincerely,

Lanying Liang and Yuefeng Liu
