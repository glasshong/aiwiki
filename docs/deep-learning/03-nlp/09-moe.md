# MoE

MoE는 Mixture of Experts의 약자입니다. 여러 expert network를 준비해 두고, 입력 token마다 일부 expert만 선택해서 계산하는 구조입니다.

```text
token -> router -> selected experts -> combine output
```

## 핵심 구성

- Expert: 각자 다른 패턴을 처리하는 작은 feed-forward network
- Router: token을 어떤 expert에 보낼지 결정하는 모듈
- Top-k routing: 여러 expert 중 상위 k개만 선택

## 장점

- 전체 파라미터 수를 크게 늘릴 수 있습니다.
- 매 token마다 일부 expert만 사용하므로 계산량 증가를 제한할 수 있습니다.
- 대형 언어 모델에서 capacity를 키우는 방법으로 쓰입니다.

## 문제점

- 특정 expert에 token이 몰릴 수 있습니다.
- routing과 분산 학습 구현이 복잡합니다.
- expert 간 load balancing loss가 필요할 수 있습니다.

## Dense Model과 비교

| 구분 | Dense Model | MoE |
|---|---|---|
| 계산 방식 | 모든 layer 사용 | 선택된 expert만 사용 |
| 파라미터 사용 | 매번 전체 사용 | 일부만 활성화 |
| 장점 | 단순하고 안정적 | 큰 capacity |
| 단점 | 계산량 증가 | routing 복잡도 |
