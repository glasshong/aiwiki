# Swin Transformer / DETR

Swin Transformer와 DETR은 Transformer를 Vision 문제에 맞게 변형한 대표적인 모델입니다.

## Swin Transformer

Swin은 window 단위 Attention과 shifted window를 사용해 이미지 크기가 커질 때의 Attention 비용을 줄입니다.

## DETR

DETR은 객체 검출을 set prediction 문제로 바꿔 Transformer encoder-decoder 구조로 직접 예측합니다.

## 비교

| 구분 | Swin Transformer | DETR |
|---|---|---|
| 중심 문제 | 이미지 표현 학습 | 객체 검출 |
| 핵심 구조 | Window Attention | Transformer encoder-decoder |
| 강점 | 계층적 feature, 효율적 Attention | Detection pipeline 단순화 |
