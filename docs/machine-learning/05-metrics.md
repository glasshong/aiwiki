# 평가 지표

평가 지표는 모델이 실제 문제에서 잘 작동하는지 판단하는 기준입니다.

| 지표 | 의미 | 중요해지는 상황 |
|---|---|---|
| Accuracy | 전체 중 맞춘 비율 | 클래스가 균형적일 때 |
| Precision | 양성 예측 중 실제 양성 비율 | 오탐 비용이 클 때 |
| Recall | 실제 양성 중 찾아낸 비율 | 놓치면 안 될 때 |
| F1-score | Precision과 Recall의 조화 평균 | 두 지표의 균형이 필요할 때 |
| AUC-ROC | threshold 변화 전반의 분류 능력 | threshold 선택 전 비교 |

## 클래스 불균형

Accuracy가 높아도 좋은 모델이 아닐 수 있습니다. 양성이 1%인 문제에서 모두 음성이라고 예측해도 Accuracy는 99%가 됩니다.

이때 Precision, Recall, F1-score를 함께 봐야 합니다.
