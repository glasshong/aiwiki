# 손계산 루틴

작은 숫자로 forward, loss, backward를 직접 계산해 보면 학습 과정이 훨씬 선명해집니다.

## 기본 순서

```text
1. 입력 x를 정합니다.
2. 가중치 W와 bias b를 정합니다.
3. forward로 예측값을 계산합니다.
4. loss를 계산합니다.
5. gradient를 계산합니다.
6. learning rate를 곱해 파라미터를 업데이트합니다.
```

## 아주 작은 예시

모델이 다음과 같다고 하겠습니다.

```text
y_pred = wx + b
```

값은 다음처럼 둡니다.

```text
x = 2
y = 5
w = 1
b = 0
```

Forward:

```text
y_pred = 1 * 2 + 0 = 2
```

MSE loss:

```text
loss = (y_pred - y)^2 = (2 - 5)^2 = 9
```

Gradient:

```text
dL/dw = 2(y_pred - y)x = 2(2 - 5)2 = -12
dL/db = 2(y_pred - y) = -6
```

learning rate가 0.1이면:

```text
w_new = 1 - 0.1 * (-12) = 2.2
b_new = 0 - 0.1 * (-6) = 0.6
```

이렇게 loss를 줄이는 방향으로 파라미터가 이동합니다.
