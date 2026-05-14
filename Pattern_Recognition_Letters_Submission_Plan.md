# Pattern Recognition Letters 投稿计划

## 定位
本文建议按 **Pattern Recognition Letters (PRL)** 的短篇、聚焦型论文定位投稿，而不是作为强方法创新长文投稿。核心表述为：传统蒙古文历史档案页面级文本列检测与阅读顺序恢复的 pilot-scale low-resource benchmark。

## 主文策略
- 使用 `main_prl.tex` 作为 PRL 精简版主文。
- 标题、摘要和结论均强调 pilot-scale、layout-analysis benchmark、crop-export-ready candidate generator。
- 不声称完整 OCR 系统，不报告 CER/WER。
- 主文仅保留关键表格：数据统计、主结果、TP/FP/FN+AP、严格页面级指标。
- RT-DETR、DocLayout-YOLO、详细 IAA、阈值、训练规模、column-aware grid、runtime 等放入 `supplementary_prl.tex`。

## 投稿前检查
1. 确认专家转写是否已返回；若返回，补充 3 页 OCR case study。
2. 若未返回，可先投稿当前 layout benchmark 版本，并在 cover letter 中说明不报告未经验证 OCR accuracy。
3. 确认原始图像的数据共享限制表述与所在单位政策一致。
4. 上传主文、补充材料、figures、highlights 和 cover letter。

## 风险提示
- 数据规模仍小，必须保留 pilot-scale 表述。
- 完整页面成功率为 0，必须主动说明系统目前是 candidate crop generator。
- Faster R-CNN 训练预算未充分调参，必须避免过度模型排名。
