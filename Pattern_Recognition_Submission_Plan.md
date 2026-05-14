# Pattern Recognition 投稿适配计划

目标期刊：**Pattern Recognition**  
出版社：Elsevier  
期刊主页 / Guide for Authors：  
https://www.sciencedirect.com/journal/pattern-recognition/publish/guide-for-authors

## 1. 期刊匹配度判断

Pattern Recognition 覆盖 pattern recognition、computer vision、image processing、text and document analysis、neural networks 等方向。本文主题属于：

- document image analysis；
- historical archive layout analysis；
- text column detection；
- reading-order recovery；
- low-resource document analysis。

因此**方向上匹配**。但 Pattern Recognition 是方法导向较强的高水平期刊，仅作为 pilot-scale benchmark 投稿会有一定风险。

## 2. 当前稿件定位

建议投稿定位：

> A pilot-scale low-resource benchmark and evaluation protocol for traditional Mongolian historical archive text-column detection and reading-order recovery.

不建议定位为：

- 完整 OCR 系统；
- 强算法创新论文；
- 大规模 benchmark；
- state-of-the-art detection 方法论文。

## 3. 主要风险

### 风险 1：数据规模偏小

当前：

- 62 页总数据；
- 11 页测试集；
- 5 页 IAA；
- OCR case study 尚待专家转写。

Pattern Recognition 审稿人可能认为测试规模不足。

### 风险 2：方法创新不足

当前主方法仍是现有检测器 + rotation-aware ordering。Column-aware post-processing 是诊断实验而非性能提升。

### 风险 3：完整页面成功率为 0

这说明当前系统更适合作为 candidate crop generator，而非完全自动化 OCR preprocessing。

### 风险 4：缺少 OCR 下游验证

已准备 3 页专家转写包，但专家结果尚未返回。若能补充 CER/WER case study，会明显增强投稿说服力。

## 4. 投稿前必须完成的适配

### 4.1 使用 Elsevier / elsarticle 模板

Pattern Recognition 属于 Elsevier，建议使用 `elsarticle` 模板，而不是当前通用 `article` 模板。

需要生成：

- `main_pr_elsarticle.tex`
- `elsarticle.cls`
- `cas-model2-names.bst` 或 Elsevier 推荐 bst（视模板而定）
- figures
- references / bib 文件或内嵌参考文献

### 4.2 Highlights

Elsevier 通常要求 Highlights。当前已准备：

- `Highlights.md`

需要转换为投稿系统可上传文本或 LaTeX `highlights` 环境。

### 4.3 Graphical Abstract

Elsevier 鼓励 graphical abstract。建议使用现有 pipeline figure 或重新设计一张更适合 Pattern Recognition 的图。

候选：

- `figures/page_layout_pipeline_overview.jpg`

### 4.4 Cover Letter

当前已准备：

- `Cover_Letter_Draft.md`

需要进一步强调：

- relation to Pattern Recognition scope；
- document analysis / historical pattern recognition；
- no OCR overclaim；
- pilot-scale benchmark positioning。

### 4.5 Research highlights 和关键词

建议关键词：

- Historical document analysis
- Traditional Mongolian archives
- Text column detection
- Reading order recovery
- Low-resource document layout analysis
- Document image analysis

### 4.6 Reference style

Pattern Recognition 使用 Elsevier 风格。投稿时可用 numbered style 或 journal 自动格式化，但建议使用 `.bib` 管理参考文献。

## 5. 投稿前强烈建议补充

### 优先级 P0：专家 OCR case study

当前已准备：

`ocr_case_study_for_expert.zip`

专家返回后应加入：

- oracle crop CER/WER；
- detected crop CER/WER；
- qualitative OCR examples；
- 说明 detected crop 相比 oracle crop 的误差传播。

### 优先级 P1：补充测试页

如果能继续标注，建议把 test 从 11 页扩展到至少 30 页；如果时间允许，50 页更好。

### 优先级 P1：更强 reading-order 方法

如果要增强方法贡献，可增加：

- graph-based reading-order recovery；
- pairwise order classifier；
- column-aware learned post-processing。

## 6. 当前可立即执行的工作

1. 生成 Pattern Recognition / Elsevier `elsarticle` 投稿版。
2. 把 Cover Letter 改成 Pattern Recognition 专用版。
3. 把 Highlights 改成 Elsevier highlights 格式。
4. 准备 graphical abstract。
5. 等专家 OCR 转写返回后，补 case study。

## 7. 投稿策略建议

如果专家 OCR case study 能及时返回，建议：

- 加入 OCR case study 后投稿 Pattern Recognition。

如果专家结果短期无法返回，建议：

- 仍可投稿 Pattern Recognition，但风险较高；
- 或先投更应用型的 Q1/Q2 文档分析/文化遗产期刊。

## 8. 官方信息依据

根据 Elsevier / ScienceDirect 的 Pattern Recognition Guide for Authors，Pattern Recognition 的 scope 包含 pattern recognition、computer vision、image processing、text and document analysis、neural networks 等方向。该范围与本文 document image analysis 主题匹配，但期刊对原创性和方法严谨性要求较高。
