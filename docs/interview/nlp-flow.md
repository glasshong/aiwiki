# NLP Flow

NLP 면접 흐름은 RNN의 한계에서 Transformer가 왜 나왔는지 설명하는 방식이 가장 자연스럽습니다.

## 전체 흐름

```text
Tokenization
-> RNN / LSTM / GRU
-> Attention
-> Transformer
-> GPT / BERT
-> Efficient Attention
-> Prompting / RLHF / RAG
```

## RNN에서 시작하기

RNN은 sequence를 순서대로 읽고 hidden state를 갱신합니다.

```text
x_t + h_(t-1) -> h_t
```

한계:

- 긴 문맥에서 vanishing gradient가 생길 수 있습니다.
- 순차 계산이라 병렬화가 어렵습니다.
- 멀리 떨어진 token 관계를 직접 연결하기 어렵습니다.

## Attention으로 넘어가기

Attention은 각 token이 다른 token을 얼마나 참고할지 계산합니다.

```text
Query와 Key의 유사도 -> Value의 가중합
```

Self-attention은 같은 문장 안의 token끼리 서로를 참고합니다.

## Transformer

Transformer는 self-attention, MLP, residual connection, normalization을 쌓은 구조입니다.

```text
Embedding
-> Positional information
-> Multi-head Attention
-> MLP
-> Residual + Normalization
```

## GPT와 BERT

| 모델 | 구조 | 학습 목표 | 주 용도 |
|---|---|---|---|
| GPT | decoder-only | 다음 token 예측 | 생성 |
| BERT | encoder-only | masked token 예측 | 이해 |

GPT는 causal mask로 미래 token을 보지 못하게 합니다. BERT는 양방향 문맥을 보지만 생성 모델로 바로 쓰기에는 적합하지 않습니다.

## LLM 실무 흐름

```text
pretraining -> fine-tuning -> instruction tuning -> RLHF -> RAG / tool use
```

면접에서는 RLHF를 단독 암기하기보다 “사람이 선호하는 답변 방향으로 모델을 정렬하는 과정”으로 설명하는 것이 좋습니다.

## 면접 포인트

- RNN, LSTM, GRU가 왜 등장했는지 설명합니다.
- Attention의 Q/K/V 의미를 직관적으로 말합니다.
- Multi-head attention이 왜 여러 관계를 병렬로 볼 수 있는지 설명합니다.
- GPT와 BERT의 mask와 학습 목표 차이를 말합니다.
- RoPE, GQA, Flash Attention은 LLM 효율화 흐름 안에서 연결합니다.
