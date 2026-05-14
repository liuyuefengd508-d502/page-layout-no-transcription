# JKSU CIS 第二轮审稿意见：`main_jksu.tex`（修订稿）

**审稿角色：** 模拟审稿人，《Journal of King Saud University — Computer and Information Sciences》  
**稿件：** `main_jksu.tex`（修订后全文通读）  
**日期：** 2026-05-14  
**对照：** 首轮意见见 `JKSU_CIS_Peer_Review_main_jksu.md`

---

## 总体推荐（修订后）

**小修后可接受（Minor revision）** 或 **录用前须改一处笔误（Accept pending correction）**。

与首轮相比，作者在**方法透明度、局限性坦诚度、可复现性披露、结论对领域内/领域外贡献的切分**上做了实质性加强，回应了多数「Major」层面的关切。稿件仍属**试点/诊断型应用研究**，数据规模与验证集大小的根本限制未消失，但叙述与自我限定已与之匹配。

---

## 已较好回应的首轮意见（Acknowledgement）

1. **配对阅读顺序指标的局限性**  
   在「Rotation-Aware Reading-Order Recovery」小节中明确：该指标仅在匹配对上计算，属于排序模块的 **proxy**，并指出漏检难列可能导致排序分数**乐观**；将 **编辑距离 / LCS** 及与 **学习式排序**（引用 Quirós & Vidal）的对比列为未来工作——这与首轮建议一致，有利于读者正确解读表中的 RO Acc.。

2. **极小验证集与超参选择偏差**  
   讨论段新增专门段落，承认 **8 页验证集** 上选取的阈值与几何先验可能过拟合于验证分布，并提出 **k 折、留一档案夹、测试前预注册阈值** 等方向——直接回应了首轮对 val 过小的质疑。

3. **可复现性与数据可得性**  
   「Data Availability」扩展为可操作的清单：注释模式与拆分清单、预测 JSON、指标脚本与命令行入口、随机种子、优化器与学习率策略、增强与 NMS、Python/PyTorch/ultralytics 版本等；并区分「无需重训即可复现指标」与「需授权图像方可重训」——显著改善应用型论文的可审计性。

4. **结论中贡献的层次化**  
   结论段明确区分 **（i）对传统蒙古文档案社区** 的三条贡献（协议、bootstrap 不确定度下的评估包、相对启发式的 F1 提升）与 **（ii）对更广文档分析社区** 的诊断信息（迁移基线需公平训练预算，DocLayout-YOLO 50 epoch 示例）；同时承认 **未提出新检测架构或学习式阅读顺序模块**、整页成功率仍低——边界清晰，与「pilot study」定位一致。

5. **伦理与展示图**  
   伦理声明补充历史印章/机构标记作为版式噪声（Ignore）处理、不用于识别现代人敏感属性，并说明示例图已获馆藏机构发表许可——回应了首轮 minor 建议。

6. **诊断表与测试域**  
   阈值敏感性、column-aware、消融等表的 caption 中已多处标明 **original 11-page test** 或验证用途，与 **54 页扩展测试主结果** 的区分更清晰（阈值表 caption 除外，见下节「须修正」）。

---

## 须在录用前修正的问题（Critical / Must fix）

### 验证集页数与表题不一致

- 正文与统计表写明 **validation 为 8 页**（`tab:data_stats` 及讨论中「8 pages」）。  
- 但 `tab:threshold` 的标题为：「Validation threshold sensitivity … on the **original 11-page validation split**」——**「11-page」与「validation」被错误拼接**：11 页在本项目中对应 **original test**，验证集应为 **8 页**。

**建议：** 将表题改为例如「… on the **8-page validation split**」或「… on the **validation split (8 pages)**」，并与正文「8 validation pages」严格一致，避免审稿人与读者对数据划分产生根本性质疑。

---

## 仍建议在修回中考虑的内容（Major 弱化后 / Minor）

1. **主测试域与迁移基线仍不一致**  
   迁移基线（RT-DETR、DocLayout-YOLO）仍在 **11 页 original test** 上报告；主检测对比在 **54 页 expanded test**。讨论已说明诊断性质，但若修回周期允许，**至少补充一行**「在扩展测试上同一协议下的 DocLayout-YOLO 50ep」或脚注说明「算力/时间限制未在扩展集重评」会更闭环。

2. **「未来工作」与当前承诺的平衡**  
   已提出 k-fold、LCS/编辑距离等未来方向；若编辑部要求「修回必须包含实验」，作者需评估是否能在修回中完成 **最小可行** 的交叉验证或序列级顺序指标之一。若不能，保持现状亦可，但建议在 Cover letter 中一句说明资源边界。

3. **结论用词**  
   结论中「**outperforms** a classical heuristic baseline」在数值支撑下可接受；若希望进一步降低「竞赛式」语感，可改为「achieves higher F1 than … under the reported protocol」，与全文 diagnostic 语气完全一致。

4. **参考文献**  
   体量仍偏紧凑；若篇幅允许，可增补 3–6 条近年 **historical layout / reading order / low-resource DIA** 文献，以强化与 JKSU CIS 一般读者的对话。

5. **Data Availability 中的版本号**  
   所列 PyTorch、ultralytics 等版本应确保与**实际产生表格结果**的训练环境一致；若后续升级环境，建议在提交前再次核对，避免「可复现声明」与日志不符。

---

## 第二轮总体结论

修订稿在**科学诚信、方法局限披露、可复现信息、结论边界**上达到多数应用期刊对「大修」的期望；**修正阈值表 caption 中验证集页数错误**后，从技术叙述一致性角度可进入**小修/排版后录用**通道。剩余问题多为**增强性实验与文献扩展**，是否强制取决于编辑部与 AE 的严格程度。

---

*本文件为基于当前仓库内 `main_jksu.tex` 的模拟审稿，非期刊正式决定。*
