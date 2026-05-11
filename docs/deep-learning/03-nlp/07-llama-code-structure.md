# Llama 코드 구조

Hugging Face Transformers의 Llama 구현을 보면 Transformer 개념이 실제 코드 클래스들로 어떻게 나뉘는지 볼 수 있습니다.

```text
LlamaForCausalLM
└─ LlamaModel
   ├─ embed_tokens
   ├─ LlamaDecoderLayer × N
   │  ├─ LlamaRMSNorm
   │  ├─ LlamaAttention
   │  ├─ LlamaRMSNorm
   │  └─ LlamaMLP
   └─ final LlamaRMSNorm
```

## 클래스 요약

| 클래스 | 역할 | 연결 관계 |
|---|---|---|
| LlamaPreTrainedModel | 공통 기반 클래스 | LlamaModel, LlamaForCausalLM이 상속 |
| LlamaForCausalLM | 텍스트 생성용 최상위 모델 | LlamaModel + lm_head |
| LlamaModel | Llama backbone | embedding + decoder layers + final norm |
| LlamaDecoderLayer | decoder block 하나 | RMSNorm, Attention, MLP, residual 포함 |
| LlamaRMSNorm | normalization | attention 전, MLP 전, 마지막 norm에 사용 |
| LlamaAttention | self-attention | Q/K/V projection, RoPE, causal mask, KV cache |
| LlamaMLP | feed-forward network | gate/up/down projection으로 feature 변환 |

참고 구현: [Hugging Face modeling_llama.py](https://github.com/huggingface/transformers/blob/main/src/transformers/models/llama/modeling_llama.py)
