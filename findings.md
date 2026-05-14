# JKSUCIS 稿件大修发现记录


## 指标核查 - 2026-05-13
- `project16_recomputed_summary.json` 是当前 Project16 主结果来源：test GT=152；Rule F1=0.507；YOLO P/R/F1=0.956/0.717/0.820；Faster R-CNN F1=0.823。
- 摘要中的 Rule baseline 0.582 来自旧 `enhanced_layout_summary.csv`（GT=163）而非当前主评估，应改为 0.507。
- `bootstrap_ci_summary_project16.json` 中 Rule precision CI 为 [0.280, 0.611]，LaTeX 表中 [0.515,0.816] 是旧/错误值。
- `tab:imgsz_ablation` 与主结果的 image size 960 指标不一致，当前缺少可直接验证的 Project16 三尺寸重算文件；为避免冲突，第一轮应移到 supplementary 或删除主文该表。
- `tab:column_aware_diag` 表述错误：当前表内 column-aware test F1=0.825 高于 main 0.820，但 RO Acc=0.818 低于 0.900；应改成“没有稳健支配主设置/带来额外调参风险”，不能说 reduces test recall and F1。

## 贡献边界收紧 - 2026-05-13
- 将短标题和长标题统一改为 `Pilot Study` 口径，避免继续以 benchmark 自居。
- 摘要和贡献段落改为 `pilot study protocol / pilot evaluation workflow`，把核心贡献限定为注释协议、评估流程和 crop-export 接口，而不是新方法或成熟 benchmark。
- 结论句中删去 `substantially`，进一步降低效果宣称强度。

## 实验表述降级 - 2026-05-13
- 将 `substantially stronger`、`outperform` 等更强表述改为 `stronger under the current evaluation protocol`、`show stronger detection metrics`。
- 把 `benchmark` 口径进一步降为 `pilot study` / `diagnostic study`，避免与审稿意见中的“贡献边界不清”冲突。
- 继续保留主结果数值不变，但将正文语气从排名式结论转成诊断式结论。

## 二次复评修订 - 2026-05-13
- 修正 runtime 文本-表格冲突：正文不再说 YOLO 更快，而是说明 Faster R-CNN 在本地 CPU 测量中略快，runtime 仅作实现相关诊断。
- YOLOv8n vs Faster R-CNN 改为“F1 接近、置信区间重叠、非 compute-matched ranking”，避免强行宣称最好模型。
- 明确当前 62 页/11 页 test 的样本量限制，subgroup analysis 仅为 diagnostic。
- 进一步强调 complete detection 与 full-page success 均为 0，因此需要未来评估人工校正时间和下游 OCR crop 效益。
- 标注可靠性部分增加未来需要更多双人标注、adjudicated disagreement examples、Ignore subtype 可视边界的说明。

## 扩展数据集重算 - 2026-05-13
- 新增 Project 15 43 页已成功转换并合并，合并后总规模为 105 页（43 train + 8 val + 11 original test + 43 expansion test）。
- 合并后统计：TextColumn=1538，Ignore=199。
- 新的 expanded 54-page test 结果：
  - Heuristic: P/R/F1 = 0.694 / 0.753 / 0.722，RO Acc = 0.882，Complete = 0.148，Full-page success = 0.148
  - YOLOv8n: P/R/F1 = 0.936 / 0.821 / 0.875，RO Acc = 0.887，Complete = 0.111，Full-page success = 0.074
  - Faster R-CNN: P/R/F1 = 0.924 / 0.816 / 0.866，RO Acc = 0.870，Complete = 0.111，Full-page success = 0.093
- 原 11 页诊断结果仍保留在正文中作为 original-test / diagnostic 参考，但主结论与摘要已切换到 expanded 54-page 口径。

## Original-test diagnostics 统一 - 2026-05-13
- 主结果现在以 expanded 54-page test 为准。
- 原 11-page test 中的 stratified、transfer、IoU@0.75、AP、train-size、column-aware、ablation、runtime 均保留为诊断分析，并在 caption/text 中明确 original 11-page 或 diagnostic。

## Phase 1 最终审计与修正 - 2026-05-14

### 1A. main_jksu.tex 数值交叉验证
- 所有 expanded 54-page 表格数值与 findings.md 一致。
- 摘要 0.722/0.875/0.866 匹配 expanded 测试集。
- bootstrap CI 表格已使用 expanded 测试值。
- imgsz_ablation 表已从主稿件移除（不存在于 main_jksu.tex）。
- column_aware_diag 表的文本描述已调整为诊断语气。

### 1B. main.tex 和 main_prl.tex 过期数值修复
- main.tex 摘要：Rule baseline 0.582 → 0.507（11 页测试口径）。
- main.tex bootstrap CI：Rule [0.515,0.816] → [0.280,0.611]（来自 bootstrap_ci_summary_project16.json）。
- main_prl.tex 摘要：Rule baseline 0.582 → 0.507。

### 1C. supplementary_jksu.tex 重组
- 标题更新为当前 "Pilot Study" 标题。
- 新增 IAA 逐页明细表（来自 IAA_5page_per_page.csv）。
- 新增推理尺寸敏感性表（从 main.tex 移入）。
- 移除了训练协议和阈值敏感性表（在主稿件中已存在）。
- 保留 transfer baselines、IoU@0.75、training-size scaling、column-aware、ablation、runtime 作为诊断实验参考。
- pdflatex 编译通过（4 页，零警告）。

### 1D. 编译验证
- main_jksu.tex：两次 pdflatex 编译，19 页，无未解析引用，无警告。
- supplementary_jksu.tex：编译通过，4 页。

## Phase 2 实验增强 - 2026-05-14

### 2A. 公平预算迁移基线重训练
- **RT-DETR-L 50ep**：11-page test F1=0.153（5ep: 0.058），改善但领域迁移仍是瓶颈。
- **DocLayout-YOLO 50ep**：11-page test F1=**0.602**（5ep: 0.037），提升 16 倍！
  - P=0.635, R=0.572, Mean IoU=0.709, RO Acc=0.900
  - 虽然仍低于 YOLOv8n (0.820)，但从"完全无效"变为"有意义的弱基线"
  - 5ep 结果严重低估了 DocLayout-YOLO 的潜力
- 两个模型均在 MPS GPU 上训练（Mac M5 Pro）。

### 2B. YOLOv8n 多尺度重训练消融（MPS，54-page expanded test）
- imgsz 640: F1=0.875 (P=0.898, R=0.852, th=0.20)
- imgsz 960: **F1=0.888** (P=0.902, R=0.875, th=0.15) ← 最优
- imgsz 1280: F1=0.868 (P=0.931, R=0.813, th=0.25)
- 结论：960 是最优选择，验证了当前主结果。1280 高精低召。

### 2C. 论文修改
- main_jksu.tex：transfer baselines 表更新为双预算（5ep + 50ep）
- main_jksu.tex：训练协议表增加 RT-DETR 和 DocLayout-YOLO 50ep 行
- main_jksu.tex：transfer 讨论重写，强调公平比较的重要性
- supplementary_jksu.tex：新增 YOLO 多尺度重训练消融表
