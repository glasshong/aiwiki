# DL

Deep Learning은 신경망을 이용해 데이터에서 표현을 학습하는 ML의 하위 분야입니다. 전통 ML이 사람이 feature를 설계하는 비중이 크다면, DL은 여러 layer를 거치며 feature 자체를 학습합니다.

## 전체 흐름

```text
Data
-> Tensor
-> Model
-> Prediction
-> Loss
-> Gradient
-> Optimizer
-> Updated Model
-> Evaluation
```

이 흐름에서 `Loss`, `Gradient`, `Learning Rate`, `Optimizer`는 [Common Training](../common/index.md)에서 다룹니다. DL 섹션에서는 신경망 구조와 task별 모델을 중심으로 봅니다.

## 하위 구조

- [Train](01-train/index.md): activation, normalization, dropout, MLP, tensor shape
- [Vision](02-vision/index.md): CNN, classification, detection, segmentation, ViT
- [NLP](03-nlp/index.md): RNN, Transformer, Attention, GPT/BERT, LLM
- [Optimization](04-optimization/index.md): quantization, pruning, LoRA/QLoRA

## 면접용 연결 흐름

딥러닝 질문은 보통 다음 순서로 이어집니다.

```text
신경망이 왜 필요한가
-> linear layer와 activation
-> loss와 backpropagation
-> optimizer로 업데이트
-> normalization과 dropout으로 안정화
-> task에 맞는 구조 선택
```

예를 들어 CNN 질문을 받으면 convolution 자체만 말하는 것보다, “이미지는 가까운 pixel끼리 강한 관계를 가지므로 local pattern을 잘 잡는 구조가 필요했고, 그래서 convolution과 pooling이 사용된다”처럼 필요성에서 시작하는 편이 좋습니다.

## 꼭 연결해야 하는 개념

| 개념 | 연결해서 말할 것 |
|---|---|
| Activation | 선형 layer만 쌓으면 결국 하나의 선형 변환이 됨 |
| Backpropagation | chain rule로 gradient를 뒤에서 앞으로 전달 |
| Normalization | activation 분포를 안정화해 학습을 쉽게 만듦 |
| Residual Connection | 깊은 모델에서 gradient 흐름을 보조 |
| Dropout | 특정 feature에 과하게 의존하는 것을 줄임 |
| Batch Size | gradient noise, 메모리, 학습 안정성에 영향 |

## 복습 우선순위

1. 공통 학습 흐름을 먼저 이해합니다.
2. MLP와 CNN으로 layer 개념을 잡습니다.
3. Vision/NLP task별 출력 형태를 구분합니다.
4. Transformer와 Attention을 구조적으로 설명합니다.
5. 경량화와 fine-tuning은 실제 배포/실무 관점에서 연결합니다.
