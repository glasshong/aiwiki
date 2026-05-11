# ML Flow

ML 면접은 데이터, 학습 유형, 일반화, 평가 지표를 연결해서 설명하는 것이 중요합니다.

## 전체 흐름

```text
문제 정의
-> 데이터와 label 확인
-> 학습 유형 선택
-> feature / model 선택
-> regularization
-> metric 평가
```

## 학습 유형

| 유형 | 데이터 | 예시 |
|---|---|---|
| 지도 학습 | 입력과 정답 label | 분류, 회귀 |
| 비지도 학습 | 정답 없이 구조 탐색 | clustering, PCA |
| 강화 학습 | reward | 게임, 로봇, 정책 최적화 |

## 일반화

좋은 모델은 train data를 외우는 것이 아니라 새로운 데이터에도 잘 동작해야 합니다.

과적합 대응:

- L1 / L2 regularization
- data augmentation
- early stopping
- cross validation
- dropout

## PCA

PCA는 데이터의 분산을 가장 잘 보존하는 방향을 찾아 차원을 줄이는 방법입니다.

면접에서는 다음 흐름이 좋습니다.

```text
feature가 많음
-> 상관관계와 noise가 있음
-> 분산을 잘 보존하는 축으로 투영
-> 차원 축소와 시각화에 사용
```

## 평가 지표

Accuracy만으로는 부족할 수 있습니다. 특히 class imbalance가 있으면 precision, recall, F1-score, AUC-ROC를 함께 봐야 합니다.

| 지표 | 핵심 질문 |
|---|---|
| Accuracy | 전체 중 얼마나 맞췄나 |
| Precision | 양성이라고 한 것 중 진짜 양성은 얼마나 되나 |
| Recall | 실제 양성 중 얼마나 찾아냈나 |
| F1-score | precision과 recall의 균형은 어떤가 |
| AUC-ROC | threshold 변화에도 분류력이 유지되나 |

## 면접 포인트

- 지도/비지도/강화 학습 차이를 예시로 말합니다.
- L1과 L2 정규화의 차이를 weight 관점으로 설명합니다.
- PCA는 “분산을 보존하는 축으로 projection”한다고 설명합니다.
- 불균형 데이터에서는 accuracy만 보면 위험하다고 말합니다.
