# Learning Rate

Learning rate는 파라미터를 한 번에 얼마나 이동시킬지 정하는 값입니다. 너무 작으면 학습이 느리고, 너무 크면 loss가 발산하거나 좋은 지점을 지나칠 수 있습니다.

```text
parameter = parameter - learning_rate * gradient
```

## 너무 작을 때

- loss가 천천히 줄어듭니다.
- 학습 시간이 길어집니다.
- local minimum이나 plateau에서 오래 머물 수 있습니다.

## 너무 클 때

- loss가 진동하거나 발산합니다.
- 좋은 해 근처를 지나쳐 버릴 수 있습니다.
- 학습이 불안정해집니다.

## Learning Rate Scheduler

학습 내내 같은 learning rate를 쓰기보다, 단계에 따라 값을 바꾸는 경우가 많습니다.

### Warmup

초반에는 작은 learning rate로 시작해 목표 값까지 점진적으로 올립니다. 큰 모델이나 Transformer 학습에서 초반 불안정을 줄이는 데 유용합니다.

### Step Decay

정해진 epoch이나 step마다 learning rate를 일정 비율로 줄입니다.

```python
scheduler = torch.optim.lr_scheduler.StepLR(
    optimizer,
    step_size=10,
    gamma=0.1,
)
```

### Cosine Decay

learning rate를 cosine 곡선처럼 부드럽게 줄입니다.

```python
scheduler = torch.optim.lr_scheduler.CosineAnnealingLR(
    optimizer,
    T_max=100,
)
```

## PyTorch 예시

```python
import torch

optimizer = torch.optim.AdamW(model.parameters(), lr=3e-4)

for batch in dataloader:
    optimizer.zero_grad()
    loss = model(**batch).loss
    loss.backward()
    optimizer.step()
```

## Learning Rate Finder

learning rate를 작은 값에서 큰 값까지 점진적으로 올리면서 loss 변화를 보고 적절한 범위를 찾는 방법입니다. loss가 안정적으로 내려가기 시작하는 구간과 발산하기 직전 구간을 참고합니다.
