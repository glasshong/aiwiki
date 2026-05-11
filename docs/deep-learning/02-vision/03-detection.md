# Object Detection

Object Detection은 이미지 안의 객체 위치와 클래스를 함께 예측하는 task입니다.

```text
image -> detector -> bounding boxes + class labels + confidence scores
```

## 출력 형태

각 객체마다 보통 다음 정보를 예측합니다.

```text
[x_min, y_min, x_max, y_max, class, score]
```

예시:

```text
person: box=(120, 50, 300, 420), score=0.97
car: box=(330, 210, 520, 360), score=0.91
```

## 대표 구조

### Two-stage Detector

먼저 객체 후보 영역을 찾고, 그 후보를 다시 분류/보정합니다.

```text
image -> backbone -> region proposals -> ROI head -> boxes + classes
```

대표 모델:

- R-CNN
- Fast R-CNN
- Faster R-CNN
- Mask R-CNN

장점은 정확도가 좋다는 점이고, 단점은 구조가 상대적으로 복잡하고 느릴 수 있다는 점입니다.

### One-stage Detector

객체 후보 생성과 분류를 한 번에 처리합니다.

```text
image -> backbone + neck -> detection head -> boxes + classes
```

대표 모델:

- YOLO
- SSD
- RetinaNet

실시간 처리에 강합니다. YOLO 계열은 속도와 성능의 균형이 좋아 실제 서비스에서 많이 쓰입니다.

### Transformer Detector

Detection을 set prediction 문제로 보고, object query가 객체를 직접 예측합니다.

```text
image -> CNN backbone -> transformer encoder-decoder -> object queries -> predictions
```

대표 모델:

- DETR
- Deformable DETR
- DINO

DETR은 anchor와 NMS 의존도를 줄인 구조로 이해할 수 있습니다.

## Loss 구성

Detection loss는 보통 여러 loss를 합칩니다.

```text
total loss = classification loss + box regression loss + objectness loss
```

- classification loss: 객체 class를 맞히는 loss
- box regression loss: bounding box 위치를 맞히는 loss
- objectness loss: 객체가 있는지 없는지 판단하는 loss

## Metric

Detection에서는 mAP를 자주 사용합니다.

- IoU: 예측 box와 정답 box가 얼마나 겹치는지
- AP: 한 class에 대한 precision-recall 성능
- mAP: 여러 class AP의 평균

## 주의점

- 작은 객체는 놓치기 쉽습니다.
- annotation 품질이 성능에 큰 영향을 줍니다.
- confidence threshold와 NMS 설정에 따라 결과가 달라질 수 있습니다.
