# 앙상블

앙상블은 여러 모델의 예측을 결합해 더 안정적인 성능을 얻는 방법입니다.

## 주요 방식

- Bagging: 여러 모델을 병렬로 학습하고 평균 또는 투표
- Boosting: 이전 모델이 틀린 샘플에 더 집중하며 순차 학습
- Stacking: 여러 모델의 예측을 다시 메타 모델의 입력으로 사용

## 예시

- Random Forest: Bagging 계열
- XGBoost, LightGBM, CatBoost: Boosting 계열

## 장점과 단점

- 장점: 성능과 안정성이 좋아지는 경우가 많음
- 단점: 해석이 어려워지고 계산 비용이 증가할 수 있음

