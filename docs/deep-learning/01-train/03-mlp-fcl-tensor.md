# MLP / FCL / Tensor / Channel

이 문서는 딥러닝 모델을 읽을 때 자주 나오는 기본 구조와 shape 표현을 정리합니다.

## Tensor

Tensor는 딥러닝에서 데이터를 담는 다차원 배열입니다.

```text
scalar: 0차원
vector: 1차원
matrix: 2차원
tensor: n차원
```

예시:

```python
import torch

x = torch.randn(32, 3, 224, 224)
print(x.shape)
```

이미지 모델에서 위 shape는 보통 다음을 의미합니다.

```text
[batch, channel, height, width]
```

## Channel

Channel은 하나의 위치가 가진 feature 종류입니다.

- RGB 이미지: channel = 3
- 흑백 이미지: channel = 1
- CNN 중간 feature map: channel = feature 종류 수

CNN에서 channel이 커진다는 것은 더 다양한 패턴을 표현한다는 뜻입니다.

## Fully Connected Layer

Fully Connected Layer는 입력의 모든 feature가 출력의 모든 neuron과 연결되는 layer입니다. PyTorch에서는 보통 `nn.Linear`로 구현합니다.

```python
import torch
import torch.nn as nn

layer = nn.Linear(in_features=4, out_features=2)
x = torch.randn(3, 4)
y = layer(x)

print(y.shape)  # [3, 2]
```

## 이 코드가 의미하는 것

```python
layer = nn.Linear(in_features=4, out_features=2)
```

이 코드는 입력 feature 4개를 받아서 출력 feature 2개로 바꾸는 fully connected layer를 만든다는 뜻입니다.

수식으로 보면 다음과 같습니다.

```text
y = xW^T + b
```

각 shape는 다음과 같습니다.

```text
x:      [3, 4]
W:      [2, 4]
b:      [2]
y:      [3, 2]
```

여기서 `3`은 batch size입니다. 즉, 샘플 3개가 한 번에 들어왔고 각 샘플은 feature 4개를 가지고 있습니다.

```python
x = torch.randn(3, 4)
```

이 입력은 아래처럼 생각할 수 있습니다.

```text
sample 1: [f1, f2, f3, f4]
sample 2: [f1, f2, f3, f4]
sample 3: [f1, f2, f3, f4]
```

`out_features=2`이므로 각 샘플은 출력 neuron 2개의 값을 갖게 됩니다.

```text
sample 1 -> [output_1, output_2]
sample 2 -> [output_1, output_2]
sample 3 -> [output_1, output_2]
```

그래서 최종 출력 shape는 `[3, 2]`입니다.

```python
print(y.shape)  # [3, 2]
```

## 파라미터 수

`nn.Linear(4, 2)`는 weight와 bias를 학습합니다.

```text
weight: 2 * 4 = 8개
bias:   2개
total:  10개
```

코드로 확인하면 다음과 같습니다.

```python
print(layer.weight.shape)  # [2, 4]
print(layer.bias.shape)    # [2]
```

## 직관

Fully Connected Layer는 입력 feature를 섞어서 새로운 feature를 만드는 layer입니다.

예를 들어 입력 feature가 다음과 같다고 하면:

```text
[키, 몸무게, 나이, 운동량]
```

출력 feature 2개는 모델이 학습한 조합일 수 있습니다.

```text
[건강 위험 점수, 활동성 점수]
```

실제로 어떤 의미를 갖는지는 task와 학습 데이터에 따라 달라지지만, 핵심은 “입력 feature들을 가중합해서 새로운 표현을 만든다”는 점입니다.

## MLP

MLP는 Fully Connected Layer와 activation을 여러 층 쌓은 기본 신경망입니다.

```python
class MLP(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super().__init__()
        self.net = nn.Sequential(
            nn.Linear(input_dim, hidden_dim),
            nn.ReLU(),
            nn.Linear(hidden_dim, hidden_dim),
            nn.ReLU(),
            nn.Linear(hidden_dim, output_dim),
        )

    def forward(self, x):
        return self.net(x)
```

## 어디에 쓰나

- tabular data 분류/회귀
- CNN 마지막 classification head
- Transformer의 FFN 또는 MLP block
- embedding vector 후처리

## Shape 관점

MLP는 마지막 차원을 feature 차원으로 보고 변환하는 경우가 많습니다.

```python
x = torch.randn(2, 5, 16)
linear = nn.Linear(16, 32)
y = linear(x)

print(y.shape)  # [2, 5, 32]
```

즉, batch나 sequence 차원은 유지되고 feature 차원만 바뀝니다.

```text
[batch, seq_len, hidden_dim]
-> Linear(hidden_dim, new_hidden_dim)
-> [batch, seq_len, new_hidden_dim]
```

이 관점은 Transformer의 MLP block을 이해할 때 중요합니다.
