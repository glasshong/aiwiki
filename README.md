# aiwiki

ML과 DL 중심으로 AI 지식을 정리하는 Markdown 기반 문서 사이트입니다. MkDocs로 로컬 웹사이트처럼 열어볼 수 있고, 내용은 `docs/` 아래의 Markdown 파일에 계속 추가하면 됩니다.

## 구조

- [ML](docs/ml/index.md)
- [DL](docs/dl/index.md)
  - [Train](docs/dl/01-train/index.md)
  - [Vision](docs/dl/02-vision/index.md)
  - [NLP](docs/dl/03-nlp/index.md)
  - [Optimization](docs/dl/04-optimization/index.md)

## 웹사이트로 보는 방법

```powershell
pip install mkdocs
mkdocs serve
```

브라우저에서 `http://127.0.0.1:8000`을 열면 됩니다.

## 참고 출처

- AI by Hand, Prof. Tom Yeh: https://www.byhand.ai/
- Transformer - Six Levels of Understanding: https://www.byhand.ai/p/transformer-six-levels-of-understanding
- Single vs Multi-Head Attention: https://www.byhand.ai/p/library-models-attention-single-vs-multi-head
- AI by Hand Academy 소개: https://www.byhand.ai/p/ai-by-hand-academy-5ec
- Hugging Face Transformers Llama implementation: https://github.com/huggingface/transformers/blob/main/src/transformers/models/llama/modeling_llama.py
- FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness: https://arxiv.org/abs/2205.14135
- DeepNet: Scaling Transformers to 1,000 Layers: https://arxiv.org/abs/2203.00555
