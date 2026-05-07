# Normalization / Dropout / Batch Size

학습 안정성, 과적합 방지, 연산 효율을 다루는 도구들입니다.

## Normalization

활성값 분포를 안정화합니다.

- CNN: BatchNorm
- Transformer: LayerNorm, RMSNorm

## Dropout

학습 중 일부 뉴런을 꺼서 특정 경로에 대한 과도한 의존을 줄입니다.

## Batch Size

한 번의 업데이트에 사용할 샘플 수입니다.

- 작은 Batch: 노이즈가 있어 일반화에 도움이 될 수 있음
- 큰 Batch: 병렬 처리 효율이 좋지만 메모리 사용량 증가

