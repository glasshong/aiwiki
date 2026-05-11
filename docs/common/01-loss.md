# Loss Function

Loss는 모델의 예측값과 실제 정답 사이의 차이를 하나의 숫자로 표현한 값입니다. 학습은 이 loss를 줄이는 방향으로 파라미터를 업데이트하는 과정입니다.

```text
input -> model -> prediction -> loss(prediction, target) -> gradient -> update
```

## Loss가 하는 일

- 모델이 얼마나 틀렸는지 수치화합니다.
- 어떤 방향으로 가중치를 바꿔야 하는지 gradient의 기준이 됩니다.
- task의 목표를 모델이 이해할 수 있는 최적화 문제로 바꿉니다.

Loss를 잘못 고르면 모델 구조가 좋아도 학습 목표가 어긋날 수 있습니다. 예를 들어 분류 문제에 MSE를 쓰거나, 회귀 문제에 Cross Entropy를 쓰면 보통 의도한 학습이 잘 되지 않습니다.

## 대표 Loss

| 문제 유형 | 자주 쓰는 Loss | 예시 |
|---|---|---|
| 이진 분류 | Binary Cross Entropy | 스팸 여부, 질병 여부 |
| 다중 분류 | Cross Entropy | 이미지 클래스 분류 |
| 다중 라벨 분류 | BCE with Logits | 한 이미지에 여러 태그 예측 |
| 회귀 | MSE, MAE, Huber | 가격 예측, 온도 예측 |
| 언어 모델 | 다음 토큰 Cross Entropy | GPT 계열 causal LM |

## Cross Entropy

Cross Entropy는 분류 문제에서 가장 많이 쓰는 loss입니다. 정답 클래스의 확률을 높이고, 틀린 클래스의 확률을 낮추도록 학습시킵니다.

PyTorch의 `nn.CrossEntropyLoss`는 내부에서 `LogSoftmax`와 `NLLLoss`를 함께 처리합니다. 그래서 모델 출력에는 softmax를 직접 적용하지 않는 것이 일반적입니다.

```python
import torch
import torch.nn as nn

logits = torch.tensor([
    [2.0, 0.5, -1.0],
    [0.1, 1.2, 0.3],
])

targets = torch.tensor([0, 1])

criterion = nn.CrossEntropyLoss()
loss = criterion(logits, targets)

print(loss.item())
```

Shape는 보통 다음과 같습니다.

```text
logits:  [batch_size, num_classes]
targets: [batch_size]
```

정답은 one-hot vector가 아니라 class index입니다.

## Binary Cross Entropy

이진 분류에는 `BCEWithLogitsLoss`를 자주 씁니다. 이 loss는 sigmoid와 BCE를 함께 계산하므로, 모델 출력에 sigmoid를 미리 적용하지 않습니다.

```python
import torch
import torch.nn as nn

logits = torch.tensor([[1.5], [-0.7], [0.2]])
targets = torch.tensor([[1.0], [0.0], [1.0]])

criterion = nn.BCEWithLogitsLoss()
loss = criterion(logits, targets)

print(loss.item())
```

추론할 때만 sigmoid를 적용해 확률로 바꿉니다.

```python
probs = torch.sigmoid(logits)
preds = probs > 0.5
```

## Multi-label Classification

다중 클래스 분류는 여러 클래스 중 하나를 고르는 문제입니다. 반면 다중 라벨 분류는 여러 라벨이 동시에 정답일 수 있습니다.

```python
logits = torch.tensor([
    [2.0, -1.0, 0.5],
    [-0.2, 1.4, 2.1],
])

targets = torch.tensor([
    [1.0, 0.0, 1.0],
    [0.0, 1.0, 1.0],
])

criterion = nn.BCEWithLogitsLoss()
loss = criterion(logits, targets)
```

## MSE / MAE / Huber

회귀 문제에서는 연속적인 숫자를 예측합니다.

```python
import torch
import torch.nn as nn

pred = torch.tensor([2.5, 0.0, 4.0])
target = torch.tensor([3.0, -0.5, 2.0])

mse = nn.MSELoss()(pred, target)
mae = nn.L1Loss()(pred, target)
huber = nn.HuberLoss(delta=1.0)(pred, target)
```

- MSE: 큰 오차에 더 큰 penalty를 줍니다.
- MAE: 이상치에 MSE보다 덜 민감합니다.
- Huber: 작은 오차에서는 MSE처럼, 큰 오차에서는 MAE처럼 동작합니다.

## Language Model Loss

GPT 같은 causal language model은 다음 token을 맞히는 방식으로 학습합니다.

```python
import torch
import torch.nn as nn

batch_size = 2
seq_len = 4
vocab_size = 10

logits = torch.randn(batch_size, seq_len, vocab_size)
labels = torch.tensor([
    [1, 5, 2, 9],
    [3, 4, 8, 0],
])

shift_logits = logits[:, :-1, :].contiguous()
shift_labels = labels[:, 1:].contiguous()

criterion = nn.CrossEntropyLoss()
loss = criterion(
    shift_logits.view(-1, vocab_size),
    shift_labels.view(-1),
)
```

## Padding Token 무시하기

문장 길이가 다르면 padding token을 넣어 batch를 맞춥니다. 이 padding 위치까지 loss에 포함하면 모델이 의미 없는 `<pad>` 예측을 학습하게 됩니다.

```python
criterion = nn.CrossEntropyLoss(ignore_index=-100)
```

## Class Imbalance

클래스 불균형이 심하면 모델이 많은 클래스만 맞히는 방향으로 학습될 수 있습니다.

```python
class_weights = torch.tensor([1.0, 10.0])

criterion = nn.CrossEntropyLoss(weight=class_weights)
loss = criterion(logits, targets)
```

이진 분류에서는 `pos_weight`를 사용할 수 있습니다.

```python
criterion = nn.BCEWithLogitsLoss(pos_weight=torch.tensor([5.0]))
```

## 자주 하는 실수

- `CrossEntropyLoss` 전에 softmax를 적용함
- `BCEWithLogitsLoss` 전에 sigmoid를 적용함
- `CrossEntropyLoss` target에 one-hot vector를 넣음
- padding token까지 loss에 포함함
- loss 값만 보고 accuracy, F1, perplexity 같은 task metric을 함께 보지 않음
