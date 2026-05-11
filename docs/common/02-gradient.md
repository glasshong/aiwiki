# Gradient & Backpropagation

Gradient는 파라미터를 어느 방향으로 바꾸면 loss가 줄어드는지 알려주는 기울기입니다. Backpropagation은 chain rule을 이용해 출력 쪽 loss에서 입력 쪽 파라미터까지 gradient를 계산하는 과정입니다.

```text
loss -> output layer gradient -> hidden layer gradient -> parameter update
```

## Gradient Descent

가장 기본적인 업데이트는 다음과 같습니다.

```text
new_weight = old_weight - learning_rate * gradient
```

gradient가 양수이면 값을 줄이고, 음수이면 값을 키우는 방향으로 이동합니다.

## Backpropagation

모델은 여러 연산이 연결된 함수입니다. Backpropagation은 마지막 loss에서 시작해 각 연산의 미분값을 곱하며 앞쪽으로 이동합니다.

```python
import torch

x = torch.tensor([2.0], requires_grad=True)
y = x ** 2 + 3 * x

y.backward()

print(x.grad)  # dy/dx = 2x + 3 -> 7
```

## 문제 상황

- Vanishing Gradient: gradient가 너무 작아 앞쪽 layer가 거의 학습되지 않습니다.
- Exploding Gradient: gradient가 너무 커져 학습이 불안정해집니다.
- Noisy Gradient: mini-batch에 따라 업데이트 방향이 크게 흔들립니다.

## 해결책

### Gradient Clipping

gradient norm이 임계값보다 커지면 전체 gradient를 같은 비율로 줄입니다.

```python
torch.nn.utils.clip_grad_norm_(model.parameters(), max_norm=1.0)
```

### Normalization

activation 분포를 안정화해 gradient가 지나치게 커지거나 작아지는 상황을 줄입니다.

### Residual Connection

입력과 출력을 더해 gradient가 우회해서 흐를 수 있는 경로를 만듭니다.

### 적절한 초기화

Xavier, He initialization은 layer 크기와 activation 특성을 고려해 신호 크기가 지나치게 변하지 않도록 초기화합니다.
