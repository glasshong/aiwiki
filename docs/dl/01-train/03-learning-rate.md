# Learning Rate

Learning Rate는 파라미터를 한 번에 얼마나 이동시킬지 정하는 값입니다.

## 너무 작으면

학습이 안정적이지만 느립니다.

## 너무 크면

Loss가 발산하거나 좋은 지점을 지나칠 수 있습니다.

## 해결책

### Warmup

초반에 작은 Learning Rate로 시작해 목표 값까지 점진적으로 키웁니다.

### Cosine decay

Learning Rate를 부드럽게 줄여 후반 수렴을 안정화합니다.

### Step decay

정해진 step마다 Learning Rate를 낮춥니다.

### Learning rate finder

Learning Rate를 작은 값에서 큰 값까지 증가시키며 Loss 변화를 보고 적절한 범위를 찾습니다.
