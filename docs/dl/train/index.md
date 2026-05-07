# Train

Train은 DL 모델을 학습시키는 전체 과정입니다. 데이터가 모델을 통과하고, Loss가 계산되고, Gradient와 Optimizer가 파라미터를 갱신합니다.

## 핵심 주제

- [Loss Function](loss.md)
- [Gradient & Backpropagation](gradient.md)
- [Learning Rate](learning-rate.md)
- [Optimizer](optimizer.md)
- [Activation](activation.md)
- [Normalization / Dropout / Batch Size](training-tools.md)
- [손계산 루틴](by-hand.md)

## 기본 루프

```text
1. 입력 데이터를 모델에 넣는다.
2. 모델이 예측값을 만든다.
3. Loss로 예측과 정답의 차이를 계산한다.
4. Backpropagation으로 Gradient를 구한다.
5. Optimizer가 파라미터를 업데이트한다.
6. 검증 데이터로 일반화 성능을 확인한다.
```

