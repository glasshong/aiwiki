# Segmentation

Segmentation은 이미지의 각 pixel이 어떤 class 또는 객체에 속하는지 예측하는 task입니다.

```text
image -> segmentation model -> pixel-level mask
```

## 종류

### Semantic Segmentation

각 pixel의 class를 예측합니다.

```text
road, sky, car, person
```

같은 class의 객체는 하나로 취급합니다.

### Instance Segmentation

객체 instance를 구분합니다.

```text
person #1, person #2, car #1
```

같은 사람 class라도 서로 다른 객체로 분리합니다.

### Panoptic Segmentation

semantic segmentation과 instance segmentation을 합친 형태입니다.

## 대표 구조

### Encoder-Decoder

이미지를 점점 압축해 의미 정보를 얻고, 다시 해상도를 복원해 mask를 만듭니다.

```text
image -> encoder -> bottleneck -> decoder -> mask
```

대표 모델:

- U-Net
- SegNet

U-Net은 encoder의 feature를 decoder로 넘기는 skip connection을 사용해 위치 정보를 보존합니다.

### Atrous / Dilated Convolution

해상도를 과하게 줄이지 않고 넓은 receptive field를 확보합니다.

대표 모델:

- DeepLabV3
- DeepLabV3+

### Transformer 기반 Segmentation

이미지 patch나 feature token 사이의 전역 관계를 attention으로 학습합니다.

대표 모델:

- SegFormer
- Mask2Former
- Segment Anything Model

## Loss

Segmentation에서는 pixel 단위 classification loss를 씁니다.

```python
import torch
import torch.nn as nn

logits = torch.randn(2, 5, 256, 256)   # [batch, classes, height, width]
masks = torch.randint(0, 5, (2, 256, 256))

loss = nn.CrossEntropyLoss()(logits, masks)
```

클래스 불균형이 심하면 Dice loss나 focal loss를 함께 쓰기도 합니다.

## Metric

자주 쓰는 지표:

- pixel accuracy
- IoU
- mean IoU
- Dice score

## 주의점

- mask annotation은 비용이 큽니다.
- 경계가 중요한 task에서는 고해상도 feature가 중요합니다.
- 작은 객체나 얇은 구조물은 쉽게 사라질 수 있습니다.
