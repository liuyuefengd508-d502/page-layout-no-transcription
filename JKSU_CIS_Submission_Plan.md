# JKSU CIS 投稿计划

## 定位
将当前工作按 **Journal of King Saud University Computer and Information Sciences** 的完整应用型论文风格组织，而不是短篇 letters 风格。论文主线保持为传统蒙古文历史档案页面级文本列检测与阅读顺序恢复。

## 主文调整
- 使用 `main_jksu.tex` 作为 Springer/JKSU 主文。
- 保留完整章节：Introduction、Related Work、Dataset and Annotation Protocol、Method、Experiments、Discussion、Conclusion。
- 继续突出：数据集与标注协议、YOLOv8n、Faster R-CNN、heuristic baseline、阅读顺序恢复。
- 继续明确：没有真实转写，不报告 CER/WER。
- 不再使用 PRL 的短篇措辞，但仍保留“candidate crop generator”“low-resource benchmark”等审慎表述。

## 投稿包
- 主文：`main_jksu.tex`
- 补充材料：`supplementary_jksu.tex`
- 投稿说明：`Cover_Letter_JKSU_CIS.md`
- 需要时可附：`Highlights_JKSU_CIS.md`、数据可用性说明、伦理声明、图表文件。

## 检查项
1. Springer 模板编译通过。
2. 作者与单位按当前通讯作者设置显示。
3. 摘要和结论不夸大 OCR 能力。
4. 结果叙事以布局分析 benchmark 为主，不宣称完整端到端 OCR。
5. 若后续专家转写返回，再补 OCR case study。
