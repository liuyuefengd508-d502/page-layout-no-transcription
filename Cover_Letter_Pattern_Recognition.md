# Cover Letter for Pattern Recognition

Dear Editor-in-Chief,

We are pleased to submit our manuscript entitled **“Layout-Aware Text Column Detection and Reading-Order Recovery for Traditional Mongolian Historical Archives”** for consideration in **Pattern Recognition**.

This manuscript addresses a low-resource document image analysis problem: page-level text-column detection and reading-order recovery for traditional Mongolian historical archives. These archives are vertically written, handwritten, visually degraded, and frequently affected by seals, background noise, and scan-orientation variation. Such characteristics make them a challenging and underrepresented case of historical document pattern recognition.

The work is positioned as a **pilot-scale low-resource benchmark and evaluation protocol**, rather than as a complete OCR system or a new detector architecture. Because expert column-level transcription is currently expensive and not yet available at scale, we focus on the upstream layout-analysis task that can be rigorously evaluated with bounding boxes and reading-order annotations. The manuscript explicitly avoids reporting CER/WER without reliable expert transcripts.

The main contributions are:

1. a page-level annotation protocol for traditional Mongolian historical archives, including TextColumn boxes, Ignore regions, scan-orientation metadata, and reading order;
2. a unified benchmark comparing heuristic extraction, YOLOv8n, Faster R-CNN MobileNetV3-FPN, and diagnostic transfer baselines;
3. transparent evaluation using TP/FP/FN counts, IoU@0.75, approximate AP, bootstrap confidence intervals, runtime, inter-annotator agreement, and stratified diagnostic analysis;
4. a crop-export-ready interface and a prepared expert-transcription package for future OCR case studies.

We believe the manuscript fits the scope of **Pattern Recognition**, particularly its interest in document analysis, image processing, and pattern recognition for challenging visual data. The study contributes to underrepresented vertical-script archival document analysis and provides a reproducible basis for future method development in low-resource historical document recognition.

The manuscript is original, has not been published elsewhere, and is not under consideration by another journal. All authors have approved this submission. The original archive images are subject to institutional access constraints; however, non-image research artifacts such as annotation schema, split manifests, evaluation scripts, configuration notes, and prediction files can be shared according to project policy.

Thank you for considering our manuscript.

Sincerely,

Lanying Liang and Yuefeng Liu
