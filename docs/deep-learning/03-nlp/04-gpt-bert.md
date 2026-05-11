# GPT / BERT

GPT와 BERT는 모두 Transformer 기반 모델이지만, 구조와 학습 목표가 다릅니다.

## 한눈에 비교

| 모델 | 구조 | Attention 방향 | 학습 목표 | 주 사용처 |
|---|---|---|---|---|
| GPT | Decoder-only | 왼쪽에서 오른쪽 | 다음 token 예측 | 생성, 대화, 요약 |
| BERT | Encoder-only | 양방향 | masked token 예측 | 분류, 검색, NER |

## GPT

GPT는 decoder-only Transformer입니다. 현재 token이 미래 token을 보지 못하도록 causal mask를 사용하고, 다음 token을 맞히는 방식으로 학습합니다.

```text
나는 밥을 -> 먹었다
```

핵심 특징:

- causal language modeling
- auto-regressive generation
- decoder block 사용
- prompt를 조건으로 다음 token을 반복 생성

생성 과정:

```text
prompt -> logits -> next token sampling -> prompt에 추가 -> 반복
```

## BERT

BERT는 encoder-only Transformer입니다. 입력 문장 전체를 양방향으로 보고, 일부 token을 mask한 뒤 원래 token을 맞히도록 학습합니다.

```text
나는 [MASK]을 먹었다 -> 밥
```

핵심 특징:

- masked language modeling
- bidirectional context
- encoder block 사용
- 문장 이해 task에 강함

주 사용처:

- 문장 분류
- 감성 분석
- 개체명 인식
- 문장 유사도
- 검색 reranking

## 왜 차이가 중요한가

GPT는 미래 token을 보지 않고 다음 token을 생성해야 하므로 생성에 자연스럽습니다. 반면 BERT는 입력 전체를 양방향으로 보기 때문에 이해 task에 강하지만, 일반적인 autoregressive 생성에는 맞지 않습니다.

## Fine-tuning 방식

### GPT 계열

```text
pretraining -> instruction tuning -> preference alignment -> generation
```

### BERT 계열

```text
pretraining -> task-specific head 추가 -> supervised fine-tuning
```

예를 들어 감성 분류에서는 BERT의 `[CLS]` representation 위에 classification head를 붙여 fine-tuning합니다.

## 면접 포인트

- GPT는 decoder-only, BERT는 encoder-only입니다.
- GPT는 causal mask를 사용해 다음 token을 예측합니다.
- BERT는 양방향 문맥을 보고 masked token을 예측합니다.
- 생성은 GPT, 이해와 분류는 BERT가 기본적으로 더 자연스럽습니다.
- 최근 LLM은 GPT식 decoder-only 구조가 주류입니다.
