# JKSUCIS 稿件大修计划

## 目标
根据当前审稿意见，对 `main_jksu.tex` / `main_jksu.pdf` 进行第一轮大修：优先修复实验数值一致性、贡献定位、图表引用/可读性、复现性说明和明显表述冲突，使稿件从“内部技术报告”更接近“pilot benchmark / protocol study”投稿版本。

## 阶段
1. [completed] 核查 LaTeX 中所有指标和表格，定位不一致来源。
2. [completed] 修正文摘、正文、表格中冲突数值和不准确表述。
3. [completed] 调整贡献定位：从 full benchmark 弱化为 pilot benchmark / protocol study。
4. [completed] 改善图表排版：减少/替换 sidewaystable，放大 Figure 3 或调整说明。
5. [completed] 增强可复现性、数据受限、baseline 公平性和 reading-order metric 局限说明。
6. [completed] 重新编译并执行一致性/引用检查。

## 当前假设
- 当前投稿主文件为 `main_jksu.tex`，补充材料为 `supplementary_jksu.tex`。
- 第一轮不重新训练模型，先修稿内显著冲突；若本地已有评估脚本和结果文件，再用它们核对数值。
- 若不能找到原始评估来源，则以主结果表的最新一致口径为准，并明确弱化冲突表述。
