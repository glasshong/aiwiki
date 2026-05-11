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
