# LoRA / QLoRA

LoRA는 기존 가중치 행렬을 직접 전부 수정하지 않고, 작은 low-rank 행렬만 추가로 학습하는 fine-tuning 방법입니다.

## LoRA

전체 모델 파라미터는 고정하고 adapter 역할을 하는 작은 행렬만 학습합니다.

```text
Original weight W + small update BA
```

- 해결하는 문제: full fine-tuning은 GPU 메모리와 저장 공간을 많이 씁니다.
- 어떻게 해결하나: 학습 가능한 파라미터 수를 줄여 비용을 낮춥니다.
- 사용 예: LLM을 특정 도메인 문체, 태스크, 데이터셋에 맞출 때

## QLoRA

기반 모델을 양자화한 상태에서 LoRA를 적용하는 방식입니다.

- 해결하는 문제: 큰 LLM은 fine-tuning 시 VRAM 요구량이 큽니다.
- 어떻게 해결하나: base model은 낮은 bit로 저장하고, 작은 adapter만 학습합니다.
- 장점: 개인 GPU나 제한된 클라우드 환경에서도 LLM fine-tuning 접근성이 좋아집니다.

## LoRA 병합

학습이 끝난 adapter를 base model에 병합하면 추론 시 별도 adapter 로딩 없이 사용할 수 있습니다. 다만 여러 adapter를 바꿔가며 쓰고 싶다면 분리해서 보관하는 편이 편합니다.
