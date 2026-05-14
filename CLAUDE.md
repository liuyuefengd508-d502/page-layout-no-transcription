# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build

```bash
# Compile any of the three paper variants with pdfLaTeX:
pdflatex main.tex          # Generic/preprint version
pdflatex main_jksu.tex     # JKSU CIS journal version (uses sn-jnl.cls)
pdflatex main_prl.tex      # Pattern Recognition Letters version

# Likewise for supplementary materials:
pdflatex supplementary_jksu.tex
pdflatex supplementary_prl.tex
```

Always run `pdflatex` **twice** after changes to resolve cross-references and citations.

## Project overview

This is a LaTeX academic paper about **text-column detection and reading-order recovery for traditional Mongolian historical archives**. The work evaluates rule-based, YOLOv8n, and Faster R-CNN detectors on a custom-annotated archive dataset. The paper does NOT report OCR CER/WER because expert column-level transcripts are not available — it focuses purely on layout analysis metrics (P/R/F1@IoU 0.5, reading-order accuracy).

## Paper variants

| File | Target venue | Class | Notes |
|------|-------------|-------|-------|
| `main.tex` | Generic preprint | `article` | Original version, may be stale |
| `main_jksu.tex` | JKSU-CIS (Elsevier) | `sn-jnl` (Springer Nature) | **Active revision** — major revision in progress |
| `main_prl.tex` | Pattern Recognition Letters | `article` | Concise format (~20 pages total .tex) |

The **current active file** under revision is `main_jksu.tex` with supplementary material in `supplementary_jksu.tex`. The JKSU version uses the journal-provided `sn-jnl.cls` class file and `wrapfig.sty`.

## Supporting data files

Experimental results are stored as `.json` and `.csv` files at the repo root. The most important ones for the current revision:

- `project16_recomputed_summary.json` — 11-page **original test** results only (GT=152). Does NOT contain the expanded 54-page results.
- `project16_merge_summary.json` — Documents the Project 15+16 annotation merge that created the 105-page dataset (page-by-page column count deltas).
- `bootstrap_ci_summary_project16.json` — Bootstrap confidence intervals for the 11-page original-test metrics.
- `column_aware_val_selected_summary.json` — Column-aware detection diagnostic results.
- `column_aware_grid_top.csv` — Per-image column-aware detection output (6293 bytes).
- `ablation_ignore_order_project16.json` / `.csv` — Ablation study for ignore-region filtering and rotation-aware ordering.
- `dataset_statistics_summary.json` / `dataset_statistics_summary_after_project16_merge.json` — Dataset split and annotation statistics (62-page and 105-page versions).
- `fasterrcnn_ap_sweep_summary.json` — Faster R-CNN AP sweep results.
- `fasterrcnn_support_summary.json` — Faster R-CNN support-level metrics.
- `enhanced_layout_summary.csv` — **Old** results (GT=163), do not use for current main results.
- `project_pr_ap_sweep_project16.json` — Per-class PR and AP sweep for Project16.
- `strict_iou_metrics_project16.json` — Strict IoU metrics at multiple thresholds.
- `project_ap_summary_project16.json` — Per-class AP summary.
- `IAA_5page_per_page.csv` / `IAA_5page_summary.md` — Inter-annotator agreement results on a 5-page independent subset.

## Key manuscript facts for the revision

- Current main results use the **expanded 54-page test set** (merged from Project 15 + 16, 105 pages total: 43 train + 8 val + 54 test).
- Old 11-page test results are retained only as "original-test diagnostics"; the abstract and main conclusions now use the 54-page numbers.
- The rule-based (heuristic) baseline F1 is **0.722** (not 0.582 from the old 11-page test).
- YOLOv8n achieves 0.875 F1, Faster R-CNN 0.866 F1 on the expanded test.
- The paper is positioned as a **pilot study / diagnostic study**, NOT a benchmark — avoid "benchmark" language except when referencing diagnostic/protocol context.
- The paper explicitly does NOT report CER/WER. Do not add end-to-end OCR accuracy claims.
- All model comparison language should be diagnostic, not ranking-oriented.
- **Expanded 54-page test results are currently only documented in `findings.md`** — there is no single JSON file that directly contains them. The 11-page original test results (in `project16_recomputed_summary.json`) are kept for diagnostic tables only.
- Supplementary baselines (RT-DETR-L, DocLayout-YOLO) are in `supplementary_jksu.tex` with their training/threshold protocols. These are transfer baselines that performed poorly on this domain.

## Figures

- `figures/page_layout_pipeline_overview.jpg` — Pipeline overview (main figure)
- `figures/page_layout_annotation_example.jpg` — Annotation example
- `figures/page_layout_qualitative_failure_montage.jpg` — Qualitative failure cases

## Revision-tracking documents

- `findings.md` — Living document recording every data inconsistency, wording change, and metric correction found during the major revision. Read this first when investigating any numerical or wording question.
- `progress.md` — Chronological log of what was changed on each day of the revision.
- `task_plan.md` — Original revision plan (6 phases, all completed).
- `JKSU_CIS_Major_Revision_Response_Summary.md` — Summary of reviewer responses for the JKSU CIS submission.

## Pre-revision snapshots

Files suffixed `_before_major_revision` (e.g., `main_jksu_before_major_revision.tex`) are frozen copies of the manuscript state before the major revision began. They exist for diffing and recovery — do not edit them.

## Editing notes

- When editing LaTeX files, verify compilation with `pdflatex` at least once before claiming success.
- Metric values in the text, tables, and abstract must be cross-checked against the `.json` source files — numerical consistency has been a recurring review concern.
- The `sn-jnl` class uses `\fnm{}`, `\sur{}`, `\email{}`, `\affil[]{}` macros — do not convert these to plain `\author{}` format.
- This is **not a git repository**. There is no version control — the `_before_major_revision` snapshots are the only backup mechanism. Consider suggesting `git init` if making further changes.
- When the expanded 54-page results need verification, cross-reference `findings.md` against the LaTeX tables — there is no single source-of-truth JSON for the expanded results.
