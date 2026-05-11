# Forward / Backward

순전파와 역전파는 모델 학습의 기본 흐름입니다.

```text
input -> forward -> prediction -> loss -> backward -> gradient -> update
```

## Forward Pass

순전파는 입력 데이터를 모델에 넣어 예측값을 계산하는 과정입니다.

```python
outputs = model(inputs)
loss = criterion(outputs, targets)
```

이 단계에서는 각 layer가 입력을 받아 출력을 만들고, 마지막에 loss를 계산합니다.

## Backward Pass

역전파는 loss에서 시작해 각 파라미터가 loss에 얼마나 영향을 줬는지 gradient를 계산하는 과정입니다.

```python
loss.backward()
```

PyTorch는 forward 과정에서 연산 그래프를 저장해 두었다가 `backward()`가 호출되면 chain rule로 gradient를 계산합니다.

## 전체 학습 루프

```python
for inputs, targets in dataloader:
    optimizer.zero_grad()

    outputs = model(inputs)
    loss = criterion(outputs, targets)

    loss.backward()
    optimizer.step()
```

## 자주 하는 실수

- `optimizer.zero_grad()`를 빼먹어 gradient가 계속 누적됨
- `loss.backward()` 전에 loss가 scalar인지 확인하지 않음
- evaluation 중에도 gradient를 계산해 메모리를 낭비함

평가할 때는 보통 다음처럼 gradient 계산을 끕니다.

```python
model.eval()

with torch.no_grad():
    outputs = model(inputs)
```
