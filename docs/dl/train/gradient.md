# Gradient & Backpropagation

Gradient는 각 파라미터를 어느 방향으로 바꿔야 Loss가 줄어드는지 알려주는 기울기입니다. Backpropagation은 Chain Rule로 이 기울기를 뒤에서 앞으로 계산합니다.

## 문제 상황

- Vanishing Gradient: 기울기가 너무 작아 앞쪽 Layer가 거의 학습되지 않음
- Exploding Gradient: 기울기가 너무 커져 학습이 불안정해짐

## 완화 방법

- Gradient clipping
- Normalization
- Residual connection
- 적절한 초기화

