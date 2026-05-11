# Transformer Overview

Transformer는 token 사이의 관계를 attention으로 계산하는 구조입니다. RNN처럼 순서대로 읽는 대신, 각 token이 다른 token을 얼마나 참고할지 한 번에 계산합니다.

## 왜 Transformer가 나왔나

RNN 계열은 sequence를 순서대로 처리합니다. 그래서 긴 문맥을 다루기 어렵고, 병렬화가 제한됩니다.

Transformer는 self-attention으로 모든 token 관계를 직접 계산해 이 문제를 완화합니다.

```text
RNN: 이전 hidden state를 통해 문맥 전달
Transformer: token 간 관계를 attention score로 직접 계산
```

## 기본 흐름

```text
Token
-> Embedding
-> Positional information
-> Multi-head Attention
-> Add & Norm
-> MLP / FFN
-> Add & Norm
```

## 핵심 구성 요소

### Embedding

token id를 dense vector로 바꿉니다. 모델은 이 vector 공간에서 token의 의미와 관계를 학습합니다.

### Positional Information

Transformer는 token을 한 번에 보기 때문에 순서 정보를 따로 넣어야 합니다.

- absolute positional encoding: 위치 vector를 embedding에 더함
- learned positional embedding: 위치 embedding을 학습
- RoPE: Q/K를 위치에 따라 회전시켜 상대적 위치 정보를 반영

### Self-Attention

각 token이 다른 token을 얼마나 참고할지 계산합니다.

```text
Q: 무엇을 찾는가
K: 어떤 특징을 갖고 있는가
V: 실제로 가져올 정보
```

### MLP / FFN

Attention이 token 간 정보를 섞는다면, MLP는 각 token의 feature를 비선형적으로 변환합니다.

```text
hidden_size -> ffn_dim -> hidden_size
```

### Residual + Normalization

깊은 모델에서 gradient 흐름을 안정화하고 학습을 쉽게 만듭니다.

## 주요 하이퍼파라미터

- `hidden_size`: token 하나를 표현하는 전체 vector 차원
- `num_attention_heads`: attention을 몇 개의 head로 나누는지
- `head_dim`: head 하나가 담당하는 차원
- `num_layers`: encoder 또는 decoder block을 몇 층 쌓는지
- `ffn_dim`: attention 뒤의 feed-forward network 내부 차원

보통 다음 관계를 가집니다.

```text
head_dim = hidden_size / num_attention_heads
```

## Positional Encoding과 RoPE

| 구분 | Positional Encoding | RoPE |
|---|---|---|
| 방식 | 위치 벡터를 embedding에 더함 | Q/K 벡터를 위치에 따라 회전 |
| 반영 위치 | 입력 embedding 단계 | attention의 Q/K 단계 |
| 강점 | 구조가 단순하고 직관적 | 상대적 위치 관계를 attention score에 자연스럽게 반영 |

RoPE는 Llama 계열처럼 긴 문맥을 다루는 decoder-only LLM에서 자주 등장합니다.

## Encoder와 Decoder

| 구조 | 특징 | 대표 모델 |
|---|---|---|
| Encoder-only | 입력 전체를 양방향으로 이해 | BERT |
| Decoder-only | 이전 token만 보고 다음 token 생성 | GPT, Llama |
| Encoder-Decoder | 입력을 이해하고 출력 sequence 생성 | T5, Transformer 원 논문 구조 |

## 면접 포인트

- Transformer는 RNN의 순차 처리 한계를 attention으로 완화합니다.
- Self-attention은 token 간 관계를 직접 계산합니다.
- Multi-head attention은 여러 관계 패턴을 병렬로 봅니다.
- Positional information이 없으면 순서 정보를 알 수 없습니다.
- GPT와 BERT의 차이는 Transformer block의 사용 방식과 학습 목표에서 나옵니다.
