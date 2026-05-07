# Swin Transformer / DETR

Swin Transformer와 DETR은 Transformer를 Vision 문제에 맞게 변형한 대표적인 모델입니다.

## Swin Transformer

Swin Transformer는 이미지를 작은 window 단위로 나누어 Attention을 계산합니다. 일반 ViT처럼 모든 patch가 한 번에 서로를 보는 방식은 이미지 크기가 커질수록 계산량이 빠르게 증가합니다. Swin은 window 내부에서만 Attention을 계산하고, 다음 Layer에서 window 위치를 이동시키는 shifted window 방식을 사용해 효율과 표현력을 함께 잡습니다.

## 핵심 아이디어

- Window-based Self-Attention: 전체 이미지가 아니라 작은 window 안에서 Attention 계산
- Shifted Window: 다음 Layer에서 window를 이동시켜 서로 다른 window 간 정보 교환
- Hierarchical Feature Map: CNN처럼 단계가 깊어질수록 해상도는 줄고 채널은 늘어남
- 다양한 Vision task에 적용 가능: classification, detection, segmentation

## 왜 중요한가

Swin Transformer는 Transformer 구조를 이미지의 계층적 특성에 맞게 조정했습니다. CNN의 장점인 계층적 feature map과 Transformer의 Attention 구조를 절충한 모델로 볼 수 있습니다.

## DETR

DETR은 Detection Transformer의 약자입니다. 기존 object detection은 anchor, proposal, NMS 같은 후처리 요소가 많이 필요했습니다. DETR은 객체 검출을 set prediction 문제로 바꿔 Transformer encoder-decoder 구조로 직접 예측합니다.

## DETR의 흐름

```text
Image
→ CNN backbone
→ Feature map
→ Transformer encoder-decoder
→ Object queries
→ Class + Bounding box
```

## 핵심 아이디어

- Object Query: 찾고 싶은 객체 후보를 query 형태로 둠
- Set Prediction: 순서 없는 객체 집합을 예측
- Bipartite Matching: 예측 박스와 실제 박스를 일대일로 매칭
- NMS 의존 감소: 중복 박스 제거 후처리를 줄임

## Swin과 DETR 비교

| 구분 | Swin Transformer | DETR |
|---|---|---|
| 중심 문제 | 이미지 표현 학습 | 객체 검출 |
| 핵심 구조 | Window Attention | Transformer encoder-decoder |
| 강점 | 계층적 feature, 효율적 Attention | Detection pipeline 단순화 |
| 자주 연결되는 task | Classification, Detection, Segmentation | Object Detection |

## 공부할 때 보는 순서

1. ViT에서 patch token 개념을 먼저 이해합니다.
2. 이미지 크기가 커질 때 full Attention 비용이 왜 커지는지 봅니다.
3. Swin의 window attention과 shifted window가 이 문제를 어떻게 줄이는지 봅니다.
4. Detection task에서 box prediction이 왜 어려운지 봅니다.
5. DETR이 object query와 matching으로 detection을 어떻게 단순화하는지 봅니다.

