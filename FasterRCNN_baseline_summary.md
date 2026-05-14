# Faster R-CNN Baseline Summary

## 实验目的

为回应 Q1 审稿意见中“缺少强 detector baseline”的问题，新增 torchvision Faster R-CNN MobileNetV3-FPN baseline。

## 设置

- Model: Faster R-CNN MobileNetV3-FPN
- Initialization: COCO-pretrained torchvision weights
- Head: replaced with 2-class head, background + TextColumn
- Training split: 43 train pages
- Validation split: 8 val pages
- Test split: 11 test pages
- Epochs: 5
- Learning rate: 0.0005
- Image max-side: 960
- Threshold selection: selected on val split
- Best val threshold: 0.8

## 结果

### Val-selected test result

| Method | Threshold | P | R | F1 | Mean IoU | RO Acc. |
|---|---:|---:|---:|---:|---:|---:|
| Faster R-CNN MobileNet | 0.8 | 0.917 | 0.681 | 0.782 | 0.738 | 0.860 |

### 对比当前主表

| Method | P | R | F1 | Mean IoU | RO Acc. |
|---|---:|---:|---:|---:|---:|
| Rule proposed | 0.680 | 0.509 | 0.582 | 0.831 | 0.907 |
| YOLOv8n | 0.919 | 0.626 | 0.745 | 0.767 | 0.920 |
| Faster R-CNN MobileNet | 0.917 | 0.681 | 0.782 | 0.738 | 0.860 |

## 解释

Faster R-CNN 取得最高 F1 和 Recall，说明 two-stage detector 在该小数据场景下具有竞争力；YOLOv8n 仍保持最高 Precision 和 Reading-order accuracy。该结果显著增强了论文的 baseline 充分性。
