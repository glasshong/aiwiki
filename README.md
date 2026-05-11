# aiwiki

ML과 DL 중심으로 AI 지식을 정리하는 Markdown 기반 문서 사이트입니다. MkDocs로 로컬에서 웹사이트처럼 확인할 수 있고, 내용은 `docs/` 아래의 Markdown 파일에 계속 추가하면 됩니다.

## 구조

- [Common Training](docs/common/index.md)
- [ML](docs/machine-learning/index.md)
- [DL](docs/deep-learning/index.md)
  - [Train](docs/deep-learning/01-train/index.md)
  - [Vision](docs/deep-learning/02-vision/index.md)
  - [NLP](docs/deep-learning/03-nlp/index.md)
  - [Optimization](docs/deep-learning/04-optimization/index.md)

## 웹사이트로 보는 방법

```powershell
pip install mkdocs
mkdocs serve
```

브라우저에서 `http://127.0.0.1:8000`을 열면 됩니다.

## 참고 문헌

- AI by Hand, Prof. Tom Yeh: https://www.byhand.ai/
- Transformer - Six Levels of Understanding: https://www.byhand.ai/p/transformer-six-levels-of-understanding
- Single vs Multi-Head Attention: https://www.byhand.ai/p/library-models-attention-single-vs-multi-head
- AI by Hand Academy 소개: https://www.byhand.ai/p/ai-by-hand-academy-5ec
- 딥 러닝을 이용한 자연어 처리 입문 - RAG, 에이전트, 파인튜닝까지: https://wikidocs.net/book/2155
- 딥 러닝 파이토치 교과서 - 입문부터 LLM 파인튜닝까지: https://wikidocs.net/book/2788
- Hugging Face Transformers Llama implementation: https://github.com/huggingface/transformers/blob/main/src/transformers/models/llama/modeling_llama.py
- FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness: https://arxiv.org/abs/2205.14135
- DeepNet: Scaling Transformers to 1,000 Layers: https://arxiv.org/abs/2203.00555
