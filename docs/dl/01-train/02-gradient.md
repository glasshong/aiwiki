# Gradient & Backpropagation

Gradient는 파라미터를 어느 방향으로 바꿔야 Loss가 줄어드는지 알려주는 기울기입니다. Backpropagation은 Chain Rule로 이 기울기를 뒤에서 앞으로 계산합니다.

## 문제 상황

- Vanishing Gradient: 기울기가 너무 작아 앞쪽 layer가 거의 학습되지 않음
- Exploding Gradient: 기울기가 너무 커져 학습이 불안정해짐

## 해결책

### Gradient clipping

Gradient norm이 임계값보다 커질 때 전체 gradient를 같은 비율로 줄입니다. 업데이트가 한 번에 과하게 움직이지 않도록 막습니다.

### Normalization

활성값 분포를 안정화해 gradient가 너무 커지거나 작아지는 상황을 줄입니다.

### Residual connection

입력을 출력에 더해 gradient가 우회해서 흐를 수 있는 경로를 만듭니다.

### 적절한 초기화

Xavier나 He initialization은 layer 크기를 고려해 신호 크기가 지나치게 변하지 않도록 설계된 초기화 방법입니다.
