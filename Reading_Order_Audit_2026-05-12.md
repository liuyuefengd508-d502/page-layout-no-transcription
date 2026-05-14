# Reading-order audit for old 62 pages

- Annotation file: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/page_level_annotations.json`
- Pages: 62
- Valid TextColumn boxes: 931
- Ignore regions: 153
- Structural issue pages: 0
- Geometry-suspicious pages: 10
- Rotation-note-missing pages before fix: 0

## Geometry-suspicious / priority pages

- `80-48-61-1` (test): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.425, desc_inv=0.575
- `80-48-63-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.544, desc_inv=0.449
- `80-48-64-1(1)` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.614, desc_inv=0.386
- `80-48-65-1(2)` (val): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.400, desc_inv=0.600
- `80-48-69-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.308, desc_inv=0.679
- `80-48-71-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.444, desc_inv=0.556
- `80-48-72-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.505, desc_inv=0.495
- `80-48-74-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.486, desc_inv=0.514
- `80-48-75-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.714, desc_inv=0.286
- `80-48-80-1` (train_unlabeled): geometry_zigzag_review;priority_from_initial_audit; asc_inv=0.400, desc_inv=0.600

## Outputs

- Audit CSV: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/results/reading_order_audit_20260512/reading_order_audit_62_pages.csv`
- Manual checklist: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/results/reading_order_audit_20260512/reading_order_manual_review_checklist_62_pages.csv`
- Summary JSON: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/results/reading_order_audit_20260512/reading_order_audit_summary.json`
- Review images: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/results/reading_order_audit_20260512/review_images`
- Priority contact sheet: `/Users/liuyu/Desktop/mydocuments/codes/autoAIScienceforOCR/research_mongolian/page_level_ocr/results/reading_order_audit_20260512/contact_sheet_priority_10.jpg`

## Regression verification

- `validate_annotations.py`: 0 errors, 55 expected image_path warnings from JPG/rotated media versus original manifest TIFF paths.
- Backup comparison: 0 bbox changes, 0 split changes, 0 TextColumn reading_order changes, 0 Ignore changes, 0 column orientation changes.
- Applied metadata-only page note changes to 16 rotated/corrected pages.
- Rule/YOLO/Faster R-CNN test reading-order metrics are unchanged relative to the backup annotation file.

