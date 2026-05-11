# Optimizer

Optimizer는 gradient를 실제 파라미터 업데이트로 바꾸는 규칙입니다. 같은 gradient를 계산하더라도 어떤 optimizer를 쓰는지에 따라 학습 속도와 안정성이 달라집니다.

## 대표 Optimizer

| Optimizer | 특징 | 자주 쓰는 곳 |
|---|---|---|
| SGD | 단순하고 일반화가 좋은 경우가 많음 | CNN, 고전적인 학습 설정 |
| SGD + Momentum | 이전 업데이트 방향을 일부 유지 | 진동이 큰 최적화 |
| Adam | 파라미터별 adaptive learning rate 사용 | 빠른 실험, NLP, 일반 DL |
| AdamW | Adam에서 weight decay를 분리 적용 | Transformer, LLM fine-tuning |

## SGD

가장 기본적인 방식입니다.

```python
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)
```

## Momentum

이전 gradient 방향을 일부 누적해 현재 업데이트에 반영합니다. 지그재그 움직임을 줄이고 일관된 방향으로 더 빠르게 이동하게 합니다.

```python
optimizer = torch.optim.SGD(
    model.parameters(),
    lr=0.01,
    momentum=0.9,
)
```

## Adam

gradient의 평균과 제곱 평균을 추적해 파라미터마다 업데이트 크기를 다르게 조절합니다.

```python
optimizer = torch.optim.Adam(model.parameters(), lr=1e-3)
```

## AdamW

Adam의 adaptive update와 weight decay를 분리해 적용합니다. Transformer와 LLM 계열에서 기본 선택지처럼 자주 사용됩니다.

```python
optimizer = torch.optim.AdamW(
    model.parameters(),
    lr=3e-4,
    weight_decay=0.01,
)
```

## Optimizer Step 위치

일반적인 PyTorch 학습 루프는 다음 순서입니다.

```python
optimizer.zero_grad()
outputs = model(inputs)
loss = criterion(outputs, targets)
loss.backward()
optimizer.step()
```

`zero_grad()`를 빼먹으면 gradient가 batch마다 누적됩니다. gradient accumulation을 의도한 경우가 아니라면 매 step마다 초기화해야 합니다.
