# Pruning

Pruning은 중요도가 낮은 가중치, 채널, 블록을 제거해 모델을 가볍게 만드는 방법입니다.

## 비구조적 pruning

개별 weight 단위로 0으로 만듭니다. sparse 연산 지원이 있어야 실제 속도 향상이 큽니다.

## 구조적 pruning

Channel, head, block 단위로 제거합니다. 일반 하드웨어에서도 속도 개선으로 이어지기 쉽습니다.

## Fine-tuning after pruning

Pruning 후 남은 파라미터가 제거된 부분을 보완하도록 다시 학습합니다.
