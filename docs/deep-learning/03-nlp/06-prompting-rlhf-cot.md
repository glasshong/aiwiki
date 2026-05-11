# Prompting / RLHF / CoT

LLM을 실제 작업에 쓰기 위해서는 모델 자체뿐 아니라 입력 구성, 외부 지식 연결, 사람 피드백 기반 정렬이 중요합니다.

## Zero-shot

예시 없이 지시문만으로 모델이 작업을 수행하게 합니다.

```text
다음 문장을 긍정/부정으로 분류해줘: 이 제품은 생각보다 좋았다.
```

## Few-shot

프롬프트 안에 몇 개의 입력/출력 예시를 넣어 원하는 패턴을 보여줍니다.

```text
문장: 배송이 너무 느렸다.
라벨: 부정

문장: 품질이 좋고 마음에 든다.
라벨: 긍정

문장: 포장이 찢어져 있었다.
라벨:
```

## CoT

Chain-of-Thought는 모델이 중간 추론 단계를 거쳐 답하도록 유도하는 방식입니다. 복잡한 수학, 논리, 계획 문제에서 도움이 됩니다.

## Transfer Learning

Transfer Learning은 큰 데이터로 미리 학습한 모델을 다른 task나 도메인에 재사용하는 방식입니다.

```text
pretrained model -> task-specific fine-tuning -> downstream task
```

예를 들어 BERT를 사전학습한 뒤 감성 분류 데이터로 fine-tuning하면, 처음부터 학습하는 것보다 적은 데이터로 좋은 성능을 얻을 수 있습니다.

## Reinforcement Learning

Reinforcement Learning은 agent가 environment에서 action을 선택하고 reward를 받아 더 좋은 policy를 학습하는 방법입니다.

```text
state -> action -> reward -> policy update
```

LLM에서는 사람 선호나 보상 모델을 이용해 응답 성향을 조정하는 단계와 연결됩니다.

## RLHF

Reinforcement Learning from Human Feedback은 사람의 선호 피드백을 이용해 모델 응답 성향을 조정합니다.

일반적인 흐름은 다음과 같습니다.

```text
supervised fine-tuning -> reward model training -> RL optimization
```

단순히 정답을 맞히는 것보다 유용하고 안전한 답변을 만들기 위한 정렬 과정입니다.

## RAG

Retrieval-Augmented Generation은 질문과 관련된 문서를 먼저 검색하고, 그 결과를 LLM 입력에 함께 넣어 답변을 생성하는 방식입니다.

```text
Question -> Retrieve documents -> Add context -> Generate answer
```

- 장점: 모델 파라미터에 없는 최신 정보나 사내 문서를 활용할 수 있습니다.
- 주의점: 검색 품질, chunk 크기, reranking 여부가 답변 품질에 크게 영향을 줍니다.

## Reranking

초기 검색 결과를 다시 점수화해 더 관련성 높은 문서를 위로 올리는 과정입니다. 정확도는 좋아질 수 있지만, LLM 기반 reranking은 호출 비용과 시간이 늘어날 수 있습니다.
