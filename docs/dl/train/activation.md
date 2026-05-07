# Activation

Activation은 모델에 비선형성을 넣어 복잡한 패턴을 표현하게 합니다.

## 대표 함수

- ReLU: 계산이 빠르고 기본 선택지
- GELU: Transformer 계열에서 자주 사용
- Sigmoid: 0~1 범위 출력
- Softmax: 클래스 확률 분포 출력

## 왜 필요한가

Activation이 없으면 여러 선형 Layer를 쌓아도 결국 하나의 선형 변환과 비슷해집니다.

