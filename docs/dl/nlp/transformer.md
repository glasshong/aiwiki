# Transformer & Attention

Transformer는 Attention을 중심으로 token 간 관계를 계산하는 구조입니다.

## Self-Attention

각 token이 문장 안의 다른 token을 얼마나 참고할지 계산합니다.

## Q, K, V

- Query: 찾는 관점
- Key: 비교 대상
- Value: 실제로 가져올 정보

## 단계별 이해

| 단계 | 질문 | 예시 |
|---|---|---|
| Black box | 입력과 출력은? | token → 다음 token 확률 |
| Components | 부품은? | embedding, attention, FFN |
| Tensors | shape은? | `[batch, token, hidden]` |
| Math | 핵심 수식은? | QK^T, softmax, V 가중합 |
| Coding | 최소 구현은? | NumPy attention |

