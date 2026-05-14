# Project 16 Reading-order Review Merge

更新时间：2026-05-12

## 合并结果

- 已从 Label Studio Project 16 导出旧 62 页人工复核后的标注。
- 已备份合并前主标注：`/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/page_level_annotations.before_project16_review_merge_20260512.bak`
- 已更新主标注：`/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/page_level_annotations.json`
- 已保存复核版完整副本：`/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/page_level_annotations.project16_reviewed_20260512.json`

## 新标注规模

| split | pages | TextColumn | Ignore |
|---|---:|---:|---:|
| train_unlabeled | 43 | 637 | 67 |
| val | 8 | 115 | 10 |
| test | 11 | 152 | 45 |
| total | 62 | 904 | 122 |

## 结构校验

`validate_annotations.py` 结果：0 errors，55 expected warnings。警告仍为 JPG/旋转后媒体路径与 manifest 原始 TIFF 路径不同。

全部 62 页 reading_order 已满足：TextColumn 编号为连续整数 `0..n-1`，Ignore 不参与编号。

## 快速回归指标（使用既有预测，不重新训练）

| Method | P | R | F1 | Mean IoU | RO Acc. |
|---|---:|---:|---:|---:|---:|
| Rule proposed | 0.436 | 0.605 | 0.507 | 0.826 | 0.900 |
| YOLOv8n | 0.956 | 0.717 | 0.820 | 0.770 | 0.900 |
| Faster R-CNN MobileNet | 0.912 | 0.750 | 0.823 | 0.738 | 0.818 |

说明：这些是合并后用已有预测文件重新评价的快速回归结果；投稿稿件中的所有 bootstrap、AP、IoU@0.75、消融和 LaTeX 表格应在完整重算后统一更新。
