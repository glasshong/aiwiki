# Interview Flow

면접용 복습은 개념을 많이 외우는 것보다, 질문이 들어왔을 때 자연스럽게 이어 말할 수 있는 흐름을 만드는 것이 중요합니다.

## 큰 답변 흐름

```text
문제 정의
-> 왜 이 방법이 필요한가
-> 핵심 구조
-> 장점과 한계
-> 개선 방법
-> 실제 사용 예시
```

예를 들어 Transformer를 설명할 때는 곧바로 수식부터 말하기보다, RNN의 순차 처리 한계와 long dependency 문제에서 출발하면 답변이 훨씬 자연스럽습니다.

## 섹션별 복습 순서

1. [Common Training](../common/index.md): loss, gradient, optimizer, learning rate
2. [Deep Learning Flow](dl-flow.md): 신경망 학습의 전체 흐름
3. [Vision Flow](vision-flow.md): CNN에서 ViT, Detection, Segmentation으로 확장
4. [NLP Flow](nlp-flow.md): RNN에서 Transformer, LLM, RLHF로 확장
5. [ML Flow](ml-flow.md): 전통 ML의 학습 유형, 정규화, 평가

## 면접 답변 템플릿

```text
정의:
  이 개념은 무엇인가?

필요성:
  어떤 문제를 해결하기 위해 등장했는가?

구조:
  어떤 구성 요소로 동작하는가?

장단점:
  어떤 상황에서 강하고, 어떤 한계가 있는가?

연결:
  다른 개념과 어떻게 이어지는가?
```

## 자주 이어지는 질문

| 시작 질문 | 이어질 수 있는 질문 |
|---|---|
| Loss가 뭔가요? | Cross Entropy와 MSE 차이, class imbalance 대응 |
| Backpropagation이 뭔가요? | vanishing gradient, residual connection |
| CNN이 뭔가요? | convolution, padding, pooling, receptive field |
| Transformer가 뭔가요? | self-attention, multi-head, positional encoding, RoPE |
| GPT와 BERT 차이는? | decoder-only vs encoder-only, causal LM vs MLM |
| Quantization이 뭔가요? | PTQ vs QAT, INT8/INT4, 정확도 손실 |

## 복습 팁

- 각 개념을 한 문장으로 정의합니다.
- 그림 없이도 구조를 말할 수 있게 합니다.
- 장점만 말하지 말고 한계와 보완책까지 같이 정리합니다.
- 코드 클래스 이름과 수학 개념을 연결해 둡니다.
