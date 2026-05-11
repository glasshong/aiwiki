# RNN / LSTM / GRU

RNN은 입력과 출력을 시퀀스 단위로 처리하는 모델입니다. 이전 시점의 hidden state를 다음 시점 계산에 다시 사용하므로, 문장처럼 순서가 중요한 데이터에 자연스럽게 적용됩니다.

## 핵심 구조

```text
x_t + h_(t-1) -> RNN cell -> h_t -> y_t
```

- `x_t`: 현재 시점의 입력
- `h_(t-1)`: 이전 시점의 은닉 상태
- `h_t`: 현재 시점의 은닉 상태
- `y_t`: 현재 시점의 출력

## 어디에 쓰나

- many-to-one: 감성 분류, 스팸 분류
- many-to-many: 번역, 태깅, 개체명 인식
- one-to-many: 이미지 캡셔닝처럼 하나의 입력에서 시퀀스를 생성하는 작업

## 한계

- 긴 문맥에서 gradient가 사라지거나 커질 수 있습니다.
- 시점 순서대로 계산해야 하므로 Transformer보다 병렬화가 어렵습니다.

## LSTM / GRU

LSTM과 GRU는 RNN의 장기 의존성 문제를 완화하기 위해 gate 구조를 추가한 모델입니다.

- LSTM: cell state와 input, forget, output gate를 사용합니다.
- GRU: reset gate와 update gate를 사용하며 LSTM보다 구조가 단순합니다.
