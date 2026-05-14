# JKSUCIS 稿件大修进度

## 2026-05-13
- 创建大修计划文件，开始按审稿意见核查当前稿件。
- 核对 `project16_recomputed_summary.json`、`bootstrap_ci_summary_project16.json`、`column_aware_val_selected_summary.json` 等结果来源，确认主结果应以当前 Project16 口径为准。
- 修改 `main_jksu.tex`：将论文定位调整为 pilot protocol / benchmark workflow，修正文摘、贡献、讨论和数据可得性表述，删除有冲突的 inference-size 小节。
- 将主文宽表改为普通 table 形式并重新编译通过，当前 PDF 可正常生成。
- 进一步收紧论文定位，将标题、摘要、贡献和结论统一改写为 pilot study 口径，并重新编译通过。
- 继续压低实验比较措辞，弱化排名式结论，统一为 diagnostic / pilot study 口径。
- 根据二次复评意见修正 runtime 矛盾，弱化模型比较结论，并补充公平性、小样本、实际价值和标注可靠性限制；主文和补充材料均重新编译通过。
- 扩展到 105 页的数据已合并，重新计算 expanded 54-page test 结果，并将论文主结果、数据集统计和摘要更新到新口径。
- 统一润色 main_jksu.tex 中保留的 original 11-page 表格/小节，将 stratified、transfer、IoU@0.75、AP、train-size、ablation、runtime 等旧拆分结果明确标为 diagnostic/original-test 参考，避免与 expanded 54-page 主结果混淆。
