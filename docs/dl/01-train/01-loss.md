# Loss Function

Loss는 모델의 예측값과 실제 목표값 사이의 차이를 하나의 숫자로 표현합니다.

## 자주 쓰는 Loss

- 분류: Cross Entropy
- 회귀: MSE, MAE
- 언어 모델: 다음 토큰 Cross Entropy

## 문제 상황과 해결책

### 클래스 불균형

일반 Cross Entropy는 많은 클래스에 유리할 수 있습니다. Weighted loss는 적은 클래스의 오답에 더 큰 가중치를 주어 소수 클래스를 무시하지 않게 합니다.

### 이상치가 많은 회귀

MSE는 큰 오차에 민감합니다. MAE는 이상치 영향이 작고, Huber loss는 작은 오차에서는 MSE처럼, 큰 오차에서는 MAE처럼 동작합니다.
