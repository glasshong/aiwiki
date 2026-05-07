# GPT / BERT

GPT와 BERT는 Transformer 기반이지만 목적과 구조가 다릅니다.

| 모델 | 구조 | 강점 |
|---|---|---|
| GPT | Decoder-only | 생성, 대화, 다음 토큰 예측 |
| BERT | Encoder-only | 문장 이해, 분류, 검색, NER |

## GPT

왼쪽에서 오른쪽으로 다음 token을 예측합니다.

## BERT

문장 전체를 보고 mask된 token을 복원하는 방식으로 학습합니다.

