# Loss Function

Loss는 모델의 예측값과 실제 목표값 사이의 차이를 하나의 숫자로 표현합니다. 학습은 이 숫자를 줄이는 방향으로 진행됩니다.

## 자주 쓰는 Loss

- 분류: Cross Entropy
- 회귀: MSE, MAE
- 언어 모델: 다음 토큰 Cross Entropy

## 체크포인트

- Loss가 감소해도 실제 평가 지표가 좋아지는지 확인합니다.
- 클래스 불균형이 있으면 weighted loss를 고려합니다.
- 이상치가 많으면 MAE나 Huber loss를 검토합니다.

