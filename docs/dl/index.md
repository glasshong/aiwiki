# DL

Deep Learning은 신경망을 이용해 데이터에서 표현을 학습하는 ML의 하위 분야입니다.

## 하위 구조

- [Train](01-train/index.md): 모델을 학습시키는 루프와 안정화 도구
- [Vision](02-vision/index.md): 이미지 분류, 객체 검출, 세그멘테이션
- [NLP](03-nlp/index.md): 언어 모델, Transformer, Attention
- [Optimization](04-optimization/index.md): 모델 경량화와 배포 최적화

## 기본 흐름

```text
Data
→ Tensor
→ Model
→ Prediction
→ Loss
→ Gradient
→ Optimizer
→ Updated Model
```

## ML과의 차이

ML에서는 사람이 특징을 설계하는 비중이 컸다면, DL에서는 신경망이 Layer를 거치며 표현 자체를 학습합니다.
