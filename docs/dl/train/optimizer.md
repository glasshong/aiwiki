# Optimizer

Optimizer는 Gradient를 실제 파라미터 업데이트로 바꾸는 규칙입니다.

| Optimizer | 특징 | 주 사용처 |
|---|---|---|
| SGD | 단순하고 일반화가 좋은 경우가 많음 | CNN, 고전적 학습 |
| Adam | 파라미터별 적응형 업데이트 | 빠른 실험 |
| AdamW | Weight decay를 더 안정적으로 적용 | Transformer, LLM fine-tuning |

## 실전 체크

- AdamW를 쓴다고 항상 좋은 것은 아닙니다.
- Weight decay와 Learning Rate는 함께 튜닝해야 합니다.
- 작은 데이터셋에서는 과적합을 먼저 의심합니다.

