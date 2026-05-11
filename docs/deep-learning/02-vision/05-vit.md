# ViT

ViT는 이미지를 작은 Patch로 나누고 각 Patch를 token처럼 다루는 Vision Transformer입니다.

## 흐름

```text
Image → Patch → Patch Embedding → Positional Encoding → Transformer Encoder → Head
```

## 특징

- 전역 관계를 직접 보기 쉽습니다.
- 큰 데이터셋에서 강한 성능을 보이는 경우가 많습니다.
- Patch size와 position embedding 이해가 중요합니다.
