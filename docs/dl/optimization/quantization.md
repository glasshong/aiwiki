# Quantization

Quantization은 FP32 또는 FP16 숫자를 INT8, INT4처럼 더 낮은 정밀도로 표현해 모델 크기와 연산량을 줄이는 방법입니다.

## 방식

- PTQ: 학습 후 양자화
- QAT: 학습 중 양자화 효과 반영

## 체크포인트

- 정확도 손실
- 하드웨어 지원
- activation quantization 여부
- calibration data 품질

