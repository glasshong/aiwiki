# NLP

NLP는 텍스트와 언어를 모델이 처리할 수 있는 형태로 바꾸고, 의미와 문맥을 학습해 분류, 생성, 검색, 요약 같은 작업을 수행하는 분야입니다.

## 기본 흐름

```text
Raw text -> Tokenization -> Encoding / Embedding -> Model -> Task output
```

## 핵심 개념

- 전처리: 토큰화, 정제, 정규화, 패딩처럼 텍스트를 모델 입력으로 맞추는 과정
- 언어 모델: 이전 또는 주변 문맥을 바탕으로 다음 토큰이나 가려진 토큰을 예측하는 모델
- 임베딩: 단어, 문장, 문서를 dense vector로 바꿔 의미적 유사도를 계산할 수 있게 함
- Transformer: RNN 대신 self-attention으로 문맥 관계를 병렬 계산하는 현대 NLP의 기본 구조
- RAG: 문서 검색 결과를 LLM 입력에 붙여 답변의 근거와 최신성을 보강하는 방식
- Fine-tuning: 사전 학습 모델을 특정 도메인이나 태스크에 맞게 추가 학습하는 과정
- MoE: token마다 일부 expert만 활성화해 큰 capacity를 효율적으로 쓰는 구조

## 문서

- [RNN / LSTM / GRU](01-rnn.md)
- [Transformer Overview](02-transformer-overview.md)
- [Attention 기본](03-attention-basic.md)
- [GPT / BERT](04-gpt-bert.md)
- [효율적 Attention](05-efficient-attention.md)
- [Prompting / RLHF / CoT](06-prompting-rlhf-cot.md)
- [Llama 코드 구조](07-llama-code-structure.md)
- [Autoencoder / Masked Autoencoder](08-autoencoder-mae.md)
- [MoE](09-moe.md)
