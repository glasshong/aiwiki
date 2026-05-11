# Deep Learning Flow

딥러닝 면접의 기본 흐름은 “모델이 어떻게 예측하고, 어떻게 틀린 정도를 계산하고, 어떻게 스스로 고쳐지는가”입니다.

## 전체 학습 흐름

```text
데이터
-> Tensor 변환
-> Forward pass
-> Loss 계산
-> Backward pass
-> Optimizer update
-> Metric 평가
```

## 1. 데이터가 Tensor가 된다

딥러닝 모델은 이미지, 텍스트, tabular 데이터를 그대로 이해하지 못합니다. 모든 입력은 숫자 tensor로 바뀝니다.

- 이미지: `[batch, channel, height, width]`
- 텍스트: token id sequence
- tabular: feature vector

## 2. Forward pass

모델이 입력을 layer에 통과시켜 예측값을 만듭니다.

```text
Linear / Conv / Attention -> Activation -> Normalization -> Output
```

Forward는 “현재 파라미터로 얼마나 잘 예측하는지 확인하는 단계”입니다.

## 3. Loss 계산

Loss는 예측값과 정답의 차이를 하나의 scalar로 만듭니다.

- classification: Cross Entropy
- regression: MSE, MAE, Huber
- language model: next token Cross Entropy

## 4. Backward pass

Backpropagation은 loss가 각 파라미터에 얼마나 영향을 받는지 gradient를 계산합니다.

면접에서는 다음 문장을 기억하면 좋습니다.

```text
Backpropagation은 chain rule을 이용해 loss에서 앞쪽 layer로 gradient를 전달하는 과정입니다.
```

## 5. Optimizer update

Optimizer는 gradient를 실제 파라미터 업데이트로 바꿉니다.

- SGD: 단순하지만 안정적인 기준점
- Momentum: 이전 이동 방향을 반영
- Adam: 파라미터별 adaptive update
- AdamW: weight decay를 Adam update와 분리

## 6. 일반화와 안정화

학습 loss만 낮아지는 것은 충분하지 않습니다.

- 과적합: dropout, weight decay, data augmentation
- gradient 문제: normalization, residual connection, gradient clipping
- 학습률 문제: warmup, cosine decay, scheduler

## 면접 포인트

- “loss와 metric의 차이”를 설명할 수 있어야 합니다.
- “learning rate가 너무 크거나 작으면 어떻게 되는지” 말할 수 있어야 합니다.
- “왜 normalization과 residual connection이 깊은 모델에서 중요한지” 연결할 수 있어야 합니다.
