# Normalization / Dropout / Batch Size

학습 도구들은 모델이 안정적으로 수렴하고, 과적합을 줄이며, 계산 자원을 효율적으로 쓰도록 돕습니다.

## PyTorch 학습 루프

```text
data -> model(x) -> loss -> loss.backward() -> optimizer.step() -> optimizer.zero_grad()
```

- `model(x)`: 입력으로 예측값을 계산합니다.
- `loss`: 예측값과 정답의 차이를 수치화합니다.
- `backward()`: 자동 미분으로 gradient를 계산합니다.
- `optimizer.step()`: gradient를 이용해 파라미터를 업데이트합니다.
- `zero_grad()`: 다음 step을 위해 누적 gradient를 비웁니다.

## Input Norm

모델에 들어가기 전 입력 데이터의 scale을 맞추는 전처리입니다.

## BatchNorm

mini-batch 단위로 activation의 평균과 분산을 계산해 정규화합니다. CNN에서 자주 쓰지만 작은 batch에서는 불안정할 수 있습니다.

## LayerNorm

각 sample 내부의 feature 차원 기준으로 정규화합니다. Transformer와 LLM에서 널리 쓰입니다.

### Post-LN

Residual branch를 더한 뒤 LayerNorm을 적용합니다.

### Pre-LN

Sublayer에 들어가기 전에 LayerNorm을 먼저 적용합니다. 깊은 Transformer 학습에서 더 안정적인 경우가 많습니다.

## RMSNorm

평균을 빼지 않고 root mean square 값으로 scale만 맞춥니다. Llama 계열에서 자주 등장합니다.

## QK Norm

Attention score를 계산하기 전 Query와 Key를 정규화합니다. logit이 과도하게 커져 softmax가 한쪽으로 쏠리는 문제를 줄입니다.

## GroupNorm

Channel을 여러 group으로 나누고 group 내부에서 평균과 분산을 계산합니다. 작은 batch의 Vision task에서 유용합니다.

## DeepNorm

매우 깊은 Transformer를 안정적으로 학습하기 위해 residual connection의 scale을 조정하는 방법입니다.

## Dropout

학습 중 일부 activation을 0으로 만들어 특정 feature에 과하게 의존하지 않도록 합니다.

## Batch Size

한 번의 업데이트에 사용하는 샘플 수입니다. 작은 batch는 noise가 있고, 큰 batch는 병렬 처리 효율이 좋지만 메모리를 많이 씁니다.
