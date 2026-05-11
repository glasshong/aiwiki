# Vision Flow

Vision 면접 흐름은 CNN의 inductive bias에서 시작해 task별 출력 형태로 확장하는 것이 자연스럽습니다.

## 전체 흐름

```text
CNN 기본 구조
-> Classification
-> Detection
-> Segmentation
-> ViT
-> Swin / DETR
```

## CNN에서 시작하기

CNN은 이미지의 지역 패턴을 잘 잡기 위해 convolution을 사용합니다.

- local connectivity: 가까운 pixel 관계를 봅니다.
- weight sharing: 같은 filter를 이미지 전체에 적용합니다.
- translation equivariance: 물체 위치가 조금 바뀌어도 feature가 함께 이동합니다.

## Classification

이미지 전체에 하나의 라벨을 붙이는 task입니다.

```text
image -> backbone -> global pooling -> classifier -> class
```

대표 모델:

- VGG
- ResNet
- EfficientNet
- ViT

## Detection

객체의 class와 위치를 동시에 찾습니다.

```text
image -> backbone -> detection head -> boxes + classes
```

대표 흐름:

- Faster R-CNN: two-stage detector
- YOLO: one-stage detector
- DETR: Transformer 기반 set prediction

## Segmentation

pixel 단위로 class 또는 instance를 예측합니다.

```text
image -> encoder -> decoder -> mask
```

대표 모델:

- U-Net
- DeepLab
- SegFormer
- Mask2Former
- SAM

## ViT로 넘어가는 이유

CNN은 locality bias가 강합니다. 반면 ViT는 이미지를 patch token으로 바꿔 self-attention으로 전역 관계를 학습합니다.

```text
image -> patches -> patch embeddings -> transformer encoder -> head
```

## 면접 포인트

- CNN의 convolution, padding, pooling을 그림 없이 설명할 수 있어야 합니다.
- Classification, Detection, Segmentation의 출력 차이를 먼저 말해야 합니다.
- Detection에서는 IoU와 mAP를 연결해야 합니다.
- Segmentation에서는 semantic과 instance 차이를 말할 수 있어야 합니다.
- ViT는 “이미지를 token sequence로 본다”는 관점이 핵심입니다.
