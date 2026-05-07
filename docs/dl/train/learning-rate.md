# Learning Rate

Learning Rate는 파라미터를 한 번에 얼마나 이동시킬지 정하는 값입니다.

## 너무 작으면

- 안정적이지만 학습이 느립니다.
- 좋은 지점까지 도달하는 데 오래 걸립니다.

## 너무 크면

- Loss가 발산할 수 있습니다.
- 좋은 지점을 지나칠 수 있습니다.

## 실전 패턴

- Warmup
- Cosine decay
- Step decay
- Learning rate finder

