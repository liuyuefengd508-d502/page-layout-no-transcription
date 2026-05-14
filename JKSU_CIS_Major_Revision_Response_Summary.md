# JKSU CIS 预审意见修正记录

## 已完成的无需新增实验修正

1. **标题与定位调整**
   - 标题改为强调 low-resource benchmark，弱化强方法创新暗示。
   - Introduction 明确本文是 application-oriented benchmark and protocol study，不是新检测器架构论文。

2. **摘要增加关键限制**
   - 摘要中明确写入 complete detection 和 full-page success 均为 0。
   - 明确当前系统是 candidate crop generator，而不是 fully automatic page-level OCR preprocessing system。

3. **AP 指标定义澄清**
   - 在 Evaluation Metrics 中说明 AP 不是 COCO-style mAP。
   - 改称 project-level confidence-sweep area under the precision--recall curve，并说明 ignore-region filtering 与匹配协议。

4. **阅读顺序指标解释加强**
   - 明确 pairwise reading-order accuracy 只在 matched boxes 上计算，需结合 recall 和 full-page success 解读。

5. **排版改进**
   - 宽表改为 sidewaystable。
   - 去除与 sn-jnl 不兼容的 resizebox 表格包裹。
   - 缩小表格字号并增加表格列间控制，避免 PDF 中数字粘连。

6. **术语统一**
   - 将部分 TextColumn 类别表述统一为 text-column。

## 仍需新增实验才能彻底解决的问题

1. 扩充测试集到 30--50 页。
2. 增加 10--15 页 IAA。
3. 增加小规模 OCR case study。
4. 做 compute-matched detector comparison。
5. 如有条件，增加 human-in-the-loop 校正成本实验。
