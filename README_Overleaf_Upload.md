# Overleaf 上传说明：无转写页面级版面分析论文

## 需要上传的文件

请把本文件夹 `page_layout_no_transcription_overleaf/` 中的全部内容上传到 Overleaf：

```text
main.tex
figures/page_layout_qualitative_failure_montage.jpg
README_Overleaf_Upload.md
```

## 编译方式

- Compiler: pdfLaTeX
- Main document: `main.tex`

当前版本不依赖 BibTeX，不需要上传 `.bib` 文件。

## 当前论文定位

本稿件主线已经调整为：

> 传统蒙古文历史档案页面级文本列检测、方向处理与阅读顺序恢复。

由于当前没有蒙古文专家完成手写文本转写，论文不报告 CER/WER，而是报告：

- Precision
- Recall
- F1
- Mean IoU
- Reading-order accuracy

## 注意事项

不要在该版本中增加“端到端 OCR 达到某某 CER/WER”的表述，除非后续补充真实列级转写。
