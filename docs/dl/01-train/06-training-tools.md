# Normalization / Dropout / Batch Size

학습 안정성, 과적합 방지, 연산 효율을 다루는 도구입니다.

## Input Norm

모델에 들어가기 전 입력 데이터의 scale을 맞추는 전처리입니다.

## BatchNorm

mini-batch 단위로 activation의 평균과 분산을 계산해 정규화합니다. CNN에서 자주 쓰지만 작은 batch에서는 불안정할 수 있습니다.

## LayerNorm

각 sample 내부의 feature 차원 기준으로 정규화합니다. Transformer와 LLM에서 널리 쓰입니다.

### Post-LN

Residual branch를 더한 뒤 LayerNorm을 적용합니다.

### Pre-LN

Sublayer에 들어가기 전에 LayerNorm을 먼저 적용합니다. 깊은 Transformer 학습이 더 안정적인 경우가 많습니다.

## RMSNorm

평균을 빼지 않고 root mean square 값으로 scale만 맞춥니다. Llama 계열에서 자주 등장합니다.

## QK Norm

Attention score를 계산하기 전 Query와 Key를 정규화합니다. Attention logit이 지나치게 커져 softmax가 한쪽으로 쏠리는 문제를 줄입니다.

## GroupNorm

Channel을 여러 group으로 나누고 각 group 안에서 평균과 분산을 계산합니다. 작은 batch의 Vision task에서 유용합니다.

## DeepNorm

매우 깊은 Transformer를 안정적으로 학습하기 위해 residual connection의 scale을 조정하는 방법입니다.

## Dropout

학습 중 일부 activation을 0으로 만들어 특정 feature에 과하게 의존하지 않도록 합니다.

## Batch Size

한 번의 업데이트에 사용할 샘플 수입니다. 작은 batch는 노이즈가 있고, 큰 batch는 병렬 처리 효율이 좋지만 메모리를 많이 씁니다.
