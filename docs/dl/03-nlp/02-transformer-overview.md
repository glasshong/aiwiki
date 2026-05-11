# Transformer Overview

Transformer는 token 간 관계를 Attention으로 계산하는 구조입니다.

## 핵심 구성

```text
Token → Embedding → Positional information → Attention → MLP / FFN → Normalization + Residual
```

## 먼저 볼 개념

- [Attention 기본](03-attention-basic.md)
- [효율적 Attention](05-efficient-attention.md)
- [Llama 코드 구조](07-llama-code-structure.md)

## Shape 핵심 값

- `hidden_size`: token 하나를 표현하는 전체 vector 차원
- `num_attention_heads`: attention을 몇 개 head로 나누는지
- `head_dim`: head 하나가 담당하는 차원

보통 `head_dim = hidden_size / num_attention_heads`입니다.

## Positional Encoding과 RoPE

Positional Encoding은 token 위치 정보를 embedding에 더하거나 attention 계산에 반영합니다. RoPE는 Query와 Key vector를 위치에 따라 회전시켜 상대 위치 정보가 attention score에 반영되도록 합니다.

| 구분 | Absolute Positional Encoding | RoPE |
|---|---|---|
| 위치 반영 | 위치 vector를 더함 | Q/K를 위치별 각도로 회전 |
| 정보 | 절대 위치 | 상대 위치 관계 |
| 적용 위치 | embedding 단계 | attention의 Q/K 단계 |
