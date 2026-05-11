# Hyperparameter Tuning

하이퍼파라미터는 모델이 학습으로 직접 찾지 않고 사람이 정하거나 탐색하는 설정값입니다.

## 대표 하이퍼파라미터

- learning rate
- batch size
- epoch 수
- optimizer 종류
- weight decay
- dropout rate
- hidden size, layer 수
- learning rate scheduler

## 왜 중요한가

같은 모델과 데이터라도 하이퍼파라미터에 따라 학습 안정성, 일반화 성능, 학습 시간이 크게 달라집니다.

## 주요 방법

### Manual Search

경험적으로 중요한 값부터 조금씩 바꿔 봅니다. 빠르게 감을 잡을 때 좋지만, 탐색 범위가 넓으면 비효율적입니다.

### Grid Search

정해둔 후보 조합을 모두 실험합니다.

```text
lr = [1e-2, 1e-3, 1e-4]
batch_size = [16, 32, 64]
```

조합 수가 빠르게 늘어나는 것이 단점입니다.

### Random Search

범위 안에서 무작위로 값을 뽑아 실험합니다. 모든 조합을 훑는 것보다 효율적인 경우가 많습니다.

### Bayesian Optimization

이전 실험 결과를 바탕으로 다음에 시도할 값을 똑똑하게 고릅니다. 실험 비용이 큰 모델에서 유용합니다.

## 실무 순서

1. 먼저 작은 데이터나 짧은 epoch으로 빠르게 확인합니다.
2. learning rate와 batch size를 먼저 맞춥니다.
3. 과적합이면 weight decay, dropout, data augmentation을 조정합니다.
4. 성능이 안정되면 전체 데이터와 긴 학습으로 검증합니다.

## 주의점

- test set으로 튜닝하면 실제 성능을 과대평가할 수 있습니다.
- 한 번에 너무 많은 값을 바꾸면 원인을 알기 어렵습니다.
- loss뿐 아니라 task metric도 함께 봐야 합니다.
