Dear Editor,

We submit our manuscript entitled **"A Pilot Study for Text-Column Detection and Reading-Order Evaluation in Traditional Mongolian Historical Archives"** for consideration in the *ACM Journal on Computing and Cultural Heritage*.

**Context and cultural significance.** Traditional Mongolian historical archives are culturally significant, computationally underexplored documents. The script is vertically written, cursive, handwritten, and frequently degraded by aging paper, seals, stains, and scanning artifacts. Despite growing interest in digital preservation of cultural heritage, page-level layout analysis for handwritten historical Mongolian archives has received almost no attention in the literature. This work directly addresses the intersection of computing and cultural heritage that JOCCH serves.

**What we did.** We constructed a 105-page annotated dataset of traditional Mongolian archival pages, defined a page-level annotation protocol including text-column detection and Ignore regions for non-text artifacts, and compared classical heuristic extraction against YOLOv8n and Faster R-CNN detectors on an expanded 54-page test set. We further conducted fair-budget retraining of modern document-layout transfer baselines to test domain transferability. All results include bootstrap confidence intervals, strict-localization metrics, stratified subgroup analysis, and inter-annotator agreement diagnostics. The work is positioned as a pilot study in cultural heritage document analysis rather than a complete OCR system.

**Key findings.** YOLOv8n achieves F1 = 0.875 vs. 0.722 for the heuristic baseline. DocLayout-YOLO improves from F1 = 0.037 to 0.602 with fair training budget, demonstrating that modern layout priors contain transferable features but require substantial domain adaptation. Full-page success remains low (0.074), and we do not report CER/WER because expert text transcripts are unavailable.

**Fit for JOCCH.** The manuscript contributes directly to JOCCH's scope: it addresses an underrepresented cultural heritage script (traditional Mongolian), provides a documented annotation protocol for archival materials, conducts systematic computing evaluation (detector comparison, bootstrap, ablation), and honestly discusses limitations relevant to heritage digitization practice. No new detector architecture is proposed; the contribution is the pilot evaluation framework and the transparent documentation of what current computer vision tools can and cannot achieve on these culturally significant materials.

**Additional notes.** Non-image research artifacts (annotations, prediction files, evaluation scripts, training protocol) are prepared for release to maximize reproducibility despite image access restrictions. The manuscript is original, has not been published elsewhere, and is not under consideration by another journal.

Sincerely,

The Authors
