# Optimizer

Optimizer는 Gradient를 실제 파라미터 업데이트로 바꾸는 규칙입니다.

| Optimizer | 특징 | 주 사용처 |
|---|---|---|
| SGD | 단순하고 일반화가 좋은 경우가 많음 | CNN, 고전적 학습 |
| Adam | 파라미터별 적응형 업데이트 | 빠른 실험 |
| AdamW | Weight decay를 안정적으로 적용 | Transformer, LLM fine-tuning |

## 주요 개념

### Momentum

이전 gradient 방향을 일부 누적해 현재 업데이트에 반영합니다. 지그재그 움직임을 줄이고 일관된 방향의 이동을 키웁니다.

### Adam

Gradient의 평균과 제곱 평균을 추적해 파라미터마다 업데이트 크기를 다르게 조절합니다.

### AdamW

Adam의 adaptive update와 weight decay를 분리해 적용합니다.
