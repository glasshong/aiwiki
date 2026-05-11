# Optimization

Optimization 섹션은 학습된 모델을 더 작고 빠르고 저렴하게 만드는 방법을 다룹니다. 여기서의 optimization은 loss를 줄이는 optimizer가 아니라, 배포와 추론 효율을 높이는 모델 최적화에 가깝습니다.

## 왜 필요한가

큰 모델은 성능이 좋지만 다음 문제가 생깁니다.

- GPU 메모리를 많이 사용합니다.
- 추론 latency가 길어질 수 있습니다.
- 배포 비용이 큽니다.
- 모바일, 엣지 환경에 올리기 어렵습니다.

그래서 모델 크기, 연산량, 메모리 사용량을 줄이는 기법이 필요합니다.

## 핵심 기법

- [Quantization](01-quantization.md): 가중치와 activation을 낮은 bit로 표현
- [Pruning](02-pruning.md): 중요도가 낮은 가중치나 구조 제거
- [LoRA / QLoRA](03-lora.md): 전체 모델 대신 작은 adapter만 학습

## 전체 흐름

```text
large pretrained model
-> fine-tuning or adapter tuning
-> quantization
-> pruning or distillation
-> deployment
-> monitoring
```

## 기법별 감각

| 기법 | 줄이는 것 | 장점 | 주의점 |
|---|---|---|---|
| Quantization | 숫자 정밀도 | 메모리와 속도 개선 | 정확도 손실 가능 |
| Pruning | 파라미터/채널/블록 | 모델 구조 자체를 줄임 | 재학습 필요 가능 |
| LoRA | 학습 파라미터 수 | fine-tuning 비용 감소 | base model은 그대로 필요 |
| QLoRA | 학습 메모리 | 큰 LLM fine-tuning 접근성 증가 | 양자화 설정 영향 |

## 면접 포인트

- Quantization은 “값을 낮은 bit로 표현해 메모리와 연산 비용을 줄이는 것”입니다.
- Pruning은 “중요도가 낮은 연결이나 구조를 제거하는 것”입니다.
- LoRA는 “큰 가중치는 고정하고 작은 low-rank update만 학습하는 것”입니다.
- QLoRA는 “양자화된 base model 위에서 LoRA를 학습하는 것”입니다.
- 최적화 기법은 성능, 속도, 메모리 사이의 trade-off입니다.
