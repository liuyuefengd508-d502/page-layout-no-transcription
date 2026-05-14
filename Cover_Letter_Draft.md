# Cover Letter Draft

Dear Editor,

We are pleased to submit our manuscript entitled **“Layout-Aware Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives”** for consideration.

Traditional Mongolian historical archives present a distinctive page-level document-analysis challenge: the script is vertically written, handwritten, low-resource, and frequently degraded by seals, paper aging, background noise, and scan-orientation variation. In many archive digitization scenarios, expert transcription is expensive or unavailable, making full OCR evaluation difficult. Rather than reporting unverifiable OCR accuracy, this manuscript focuses on a necessary upstream task: **text-column detection and reading-order recovery** for full-page archival images.

The manuscript contributes:

1. a pilot-scale page-level annotation protocol for traditional Mongolian historical archives, including TextColumn boxes, Ignore regions, orientation metadata, and reading order;
2. a low-resource benchmark comparing heuristic extraction, YOLOv8n, Faster R-CNN MobileNetV3-FPN, and diagnostic transfer baselines under unified project-level evaluation;
3. transparent evaluation with TP/FP/FN counts, IoU@0.75, approximate AP, bootstrap confidence intervals, runtime, stratified diagnostic analysis, and inter-annotator agreement on a subset;
4. a crop-export-ready interface and a prepared small OCR case-study package for future expert-transcribed evaluation.

We explicitly frame the work as a **pilot-scale layout-analysis benchmark**, not as a complete OCR system. Because column-level expert transcripts are not yet available, the paper does not report CER/WER. Instead, it provides a reproducible evaluation protocol and crop-export interface that can support downstream OCR experiments once reliable transcripts are obtained.

We believe this study will be of interest to readers working on document analysis, historical archive digitization, low-resource OCR preprocessing, and cultural-heritage AI. The work is especially relevant for underrepresented vertical-script archival materials, where page-level layout analysis remains underexplored.

The manuscript is original, has not been published elsewhere, and is not under consideration by another journal. All authors have approved the submission. Archive images are subject to institutional access constraints, but the annotation schema, split manifests, evaluation scripts, configuration notes, and prediction files can be shared according to project policy.

Thank you for considering our manuscript.

Sincerely,

Lanying Liang and Yuefeng Liu  
Archives, Inner Mongolia University of Science and Technology  
School of Digital and Intelligent Industry (School of Cyber Science and Technology), Inner Mongolia University of Science and Technology
