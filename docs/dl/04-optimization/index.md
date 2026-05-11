# Optimization

Optimization은 모델을 더 작고 빠르게 만들어 실제 환경에서 쓰기 좋게 만드는 과정입니다.

## 핵심 주제

- [Quantization](01-quantization.md)
- [Pruning](02-pruning.md)
- [LoRA / QLoRA](03-lora.md)

## 추천 흐름

1. 모델 크기와 추론 병목을 확인합니다.
2. Quantization으로 정밀도를 낮춥니다.
3. Pruning으로 불필요한 구조를 제거합니다.
4. LoRA/QLoRA로 fine-tuning 비용을 줄입니다.
