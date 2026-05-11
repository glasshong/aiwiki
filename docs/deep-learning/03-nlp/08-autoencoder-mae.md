# Autoencoder / Masked Autoencoder

Autoencoder는 입력을 압축했다가 다시 복원하도록 학습하는 구조입니다.

```text
input -> encoder -> latent representation -> decoder -> reconstruction
```

## Autoencoder

Autoencoder는 입력과 출력이 같은 형태입니다. 모델은 중간의 작은 latent vector에 중요한 정보를 담도록 학습합니다.

주요 사용처:

- 차원 축소
- 노이즈 제거
- 이상 탐지
- representation learning

## Denoising Autoencoder

입력에 일부러 noise를 넣고 원본을 복원하도록 학습합니다. 모델이 단순 복사가 아니라 핵심 구조를 배우도록 돕습니다.

## Masked Autoencoder

Masked Autoencoder는 입력의 일부를 가리고, 가려진 부분을 복원하도록 학습합니다.

NLP의 BERT는 masked language modeling으로 가려진 token을 맞힙니다. Vision의 MAE는 이미지 patch 일부를 가리고 복원합니다.

```text
원본 입력 -> 일부 mask -> encoder -> decoder -> masked part 복원
```

## 왜 중요한가

label 없이도 데이터 자체에서 학습 신호를 만들 수 있습니다. 그래서 대규모 사전학습에서 유용합니다.
