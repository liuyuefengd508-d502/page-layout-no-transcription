# Project 16 merged GT regression metrics (2026-05-12)

Annotations: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/page_level_annotations.json`
Test pages: 11; YOLO score threshold: 0.35; Faster R-CNN score threshold: 0.8.

## Main metrics (IoU@0.5)

| Method | Pred | GT | TP | FP | FN | P | R | F1 | mIoU | RO Acc. |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Rule proposed | 211 | 152 | 92 | 119 | 60 | 0.436 | 0.605 | 0.507 | 0.826 | 0.900 |
| YOLOv8n + rotation-aware order | 114 | 152 | 109 | 5 | 43 | 0.956 | 0.717 | 0.820 | 0.770 | 0.900 |
| Faster R-CNN | 125 | 152 | 114 | 11 | 38 | 0.912 | 0.750 | 0.823 | 0.738 | 0.818 |

## Strict IoU@0.75

| Method | P | R | F1 | mIoU | RO Acc. |
|---|---:|---:|---:|---:|---:|
| Rule proposed | 0.322 | 0.447 | 0.375 | 0.901 | 1.000 |
| YOLOv8n + rotation-aware order | 0.579 | 0.434 | 0.496 | 0.826 | 1.000 |
| Faster R-CNN | 0.352 | 0.289 | 0.318 | 0.828 | 1.000 |

## Bootstrap 95% CI (IoU@0.5)

| Method | P 95% CI | R 95% CI | F1 95% CI |
|---|---:|---:|---:|
| Rule proposed | [0.280, 0.611] | [0.488, 0.710] | [0.360, 0.647] |
| YOLOv8n + rotation-aware order | [0.908, 0.991] | [0.575, 0.830] | [0.711, 0.895] |
| Faster R-CNN | [0.844, 0.962] | [0.643, 0.844] | [0.739, 0.893] |
