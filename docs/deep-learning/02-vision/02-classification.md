# Image Classification

Image Classification은 이미지 전체에 대해 하나의 라벨 또는 여러 라벨을 예측하는 task입니다.

```text
image -> feature extractor -> classifier head -> class probability
```

## 출력 형태

단일 라벨 분류:

```text
고양이 이미지 -> cat
```

다중 라벨 분류:

```text
실내 사진 -> chair, table, window
```

## 기본 구조

### CNN 기반 구조

```text
Input image
-> convolution blocks
-> global average pooling
-> fully connected layer
-> logits
```

CNN은 작은 filter로 지역 패턴을 뽑고, layer가 깊어질수록 edge, texture, part, object-level feature를 학습합니다.

### Transformer 기반 구조

```text
Input image
-> patch embedding
-> transformer encoder
-> class token or pooled feature
-> classifier head
```

ViT는 이미지를 patch로 나누고 각 patch를 token처럼 다룹니다.

## 예시 모델

| 모델 | 구조 | 특징 |
|---|---|---|
| AlexNet | CNN | 초기 딥러닝 이미지 분류 대표 모델 |
| VGG | CNN | 단순한 3x3 convolution을 깊게 쌓음 |
| ResNet | CNN + residual | skip connection으로 깊은 모델 학습 안정화 |
| EfficientNet | CNN | depth, width, resolution을 균형 있게 scaling |
| ViT | Transformer | image patch를 token처럼 처리 |

## Loss와 Metric

단일 라벨 분류는 보통 `CrossEntropyLoss`를 사용합니다.

```python
import torch
import torch.nn as nn

logits = torch.randn(8, 10)   # [batch, num_classes]
targets = torch.randint(0, 10, (8,))

loss = nn.CrossEntropyLoss()(logits, targets)
```

자주 보는 metric:

- accuracy
- top-k accuracy
- precision / recall / F1-score
- confusion matrix

## 주의점

- 클래스 불균형이 있으면 accuracy만 보면 안 됩니다.
- train과 test 이미지 분포가 다르면 성능이 크게 떨어질 수 있습니다.
- 작은 데이터에서는 data augmentation과 pretrained model 활용이 중요합니다.
