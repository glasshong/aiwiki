# Train

Train은 DL 모델을 학습시키는 전체 과정입니다.

## 핵심 주제

- [Loss Function](01-loss.md)
- [Gradient & Backpropagation](02-gradient.md)
- [Learning Rate](03-learning-rate.md)
- [Optimizer](04-optimizer.md)
- [Activation](05-activation.md)
- [Normalization / Dropout / Batch Size](06-training-tools.md)
- [손계산 루틴](07-by-hand.md)

## 기본 루프

```text
입력 데이터
→ 모델 예측
→ Loss 계산
→ Backpropagation
→ Optimizer update
→ 평가
```
