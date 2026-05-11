# ML

Machine Learning은 데이터에서 규칙을 학습해 새로운 입력에 대한 예측이나 판단을 수행하는 방법입니다.

## 기본 흐름

```text
문제 정의
-> 데이터 수집
-> feature 구성
-> 모델 학습
-> 검증
-> 평가 지표 확인
-> 배포 또는 개선
```

## 문서

- [지도 / 비지도 / 강화 학습](01-learning-types.md)
- [L1 / L2 정규화](02-regularization.md)
- [PCA](03-pca.md)
- [앙상블](04-ensemble.md)
- [평가 지표](05-metrics.md)

## 면접용 큰 그림

ML 질문은 보통 다음 흐름으로 이어집니다.

```text
이 문제가 분류인가 회귀인가
-> label이 있는가
-> 어떤 feature를 쓰는가
-> 과적합을 어떻게 막는가
-> 어떤 metric으로 평가하는가
```

## 중요한 구분

| 질문 | 핵심 구분 |
|---|---|
| label이 있는가 | 지도 / 비지도 학습 |
| 출력이 class인가 숫자인가 | 분류 / 회귀 |
| feature가 너무 많은가 | PCA, feature selection |
| train 성능만 좋은가 | 과적합, 정규화 |
| 데이터가 불균형한가 | precision, recall, F1, AUC |

## DL과의 연결

DL도 넓게 보면 ML의 한 종류입니다. 차이는 사람이 feature를 직접 설계하는 비중이 줄고, 신경망이 layer를 통해 representation을 학습한다는 점입니다.
