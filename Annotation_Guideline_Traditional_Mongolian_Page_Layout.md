# Annotation Guideline for Traditional Mongolian Historical Archive Page Layout

## 1. Annotation Target

The primary annotation target is the **visible traditional Mongolian handwritten text column** on a full archive page. The current task is layout analysis, not transcription. Annotators should mark where each text column is located and assign its reading order.

## 2. TextColumn Box

Annotate a `TextColumn` box when the region is a target traditional Mongolian handwritten text column.

Rules:

1. Draw one bounding box around one visually coherent vertical text column.
2. Include the full visible ink area of the column, but avoid excessive background margin.
3. If one column is broken into several small vertical fragments but clearly belongs to the same reading column, annotate it as one column when the gap is small and the reading continuity is obvious.
4. If fragments are spatially separated and could be read as different columns, annotate them as separate columns.
5. Do not include seals, page borders, stains, or unrelated marks inside a TextColumn box unless they overlap the text so strongly that separation is impossible.

## 3. Reading Order

Traditional Mongolian archive columns are normally read by vertical column order across the page. In this project:

1. Assign `reading_order = 0, 1, 2, ...` from the first readable column to the last readable column.
2. For normally displayed pages, follow the visible column sequence consistently according to the dataset convention.
3. For pages rotated for annotation, assign reading order after rotation in the displayed coordinate system.
4. If two columns have ambiguous order, use the dominant page layout and record the ambiguity in notes if possible.

## 4. Orientation

Use the orientation field to describe how the displayed page relates to the expected upright reading direction:

- `correct`: the page is displayed in the expected annotation orientation.
- `rotated_90_ccw`: the original scan needed 90° counter-clockwise correction.
- `rotated_90_cw`: the original scan needed 90° clockwise correction.
- `rotated_180`: the original scan was upside down.
- `ambiguous`: orientation cannot be confidently determined.

## 5. Ignore Region

Use `Ignore` only for regions that should not be counted as text-column false positives during detector evaluation.

Recommended Ignore subtypes:

1. **seal**: red seal or stamp region.
2. **stain_noise**: paper stain, ink bleed, strong background artifact, or shadow.
3. **border_edge**: page border, scanning edge, binding shadow, or black margin.
4. **non_target_language**: Chinese handwritten archive image or non-target-language text region mixed into the source folder.
5. **ambiguous_fragment**: fragmentary strokes that may be text but are too incomplete to define a column.
6. **overlap_unseparable**: artifact strongly overlaps text and cannot be cleanly separated.

Important:

- Do not mark a normal target text column as Ignore merely because it is faint or difficult.
- Do not use Ignore to hide detector mistakes.
- If a region contains readable target text, prefer TextColumn over Ignore.
- Ignore should be conservative and reserved for evaluation-ambiguous non-target regions.

## 6. Difficult Cases

### 6.1 Seal Over Text

If the seal overlaps but the underlying column is still identifiable, annotate the column as `TextColumn` and optionally mark the seal area as `Ignore` only if it may cause false detections.

### 6.2 Heavy Noise

If the region is clearly not text, mark it as `Ignore` only when it is visually likely to be detected as a column. Small isolated stains do not need Ignore boxes.

### 6.3 Rotated or Upside-Down Pages

Rotate the displayed image before annotation when possible. Annotate in the corrected displayed coordinate system and record the rotation state.

### 6.4 Non-target Chinese Archive Pages

If the page is a Chinese handwritten archive page rather than traditional Mongolian, exclude it from the target dataset. If it must remain in the annotation tool temporarily, mark it as `non_target_language` and do not include it in final evaluation.

## 7. Quality Check

Before submitting each page:

1. Check that every valid target text column has one TextColumn box.
2. Check that reading orders are unique and consecutive.
3. Check that Ignore is not overused.
4. Check that the page orientation is correct.
5. Check that no Chinese/non-target pages remain in the final Mongolian split.
