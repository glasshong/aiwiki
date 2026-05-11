# RNN / LSTM / GRU

RNN은 순차 데이터를 시간 순서대로 읽으면서 이전 상태를 다음 계산에 반영합니다.

## 한계

- 긴 문맥에서 gradient가 사라지거나 폭주하기 쉽습니다.
- 병렬화가 어렵습니다.

## LSTM / GRU

LSTM과 GRU는 gate 구조를 통해 중요한 정보를 더 오래 유지하려고 만든 개선형입니다.

### LSTM

Cell state와 input, forget, output gate를 사용합니다.

### GRU

Reset gate와 update gate를 사용하며 LSTM보다 구조가 단순합니다.
