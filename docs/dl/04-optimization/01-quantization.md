# Quantization

Quantization은 FP32 또는 FP16 숫자를 INT8, INT4처럼 더 낮은 정밀도로 표현해 모델 크기와 연산량을 줄이는 방법입니다.

## PTQ

Post-Training Quantization은 학습 후 양자화합니다. 빠르지만 정확도 손실이 생길 수 있습니다.

## QAT

Quantization-Aware Training은 학습 중 양자화 효과를 반영합니다. 비용은 더 들지만 정확도 손실을 줄일 수 있습니다.

## Calibration data

PTQ에서 activation 범위와 scale을 추정하기 위해 사용하는 대표 입력 데이터입니다.
