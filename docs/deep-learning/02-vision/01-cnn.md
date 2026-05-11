# CNN

CNN은 작은 filter를 이미지 위로 이동시키며 edge, texture, shape 같은 지역 특징을 추출하는 신경망 구조입니다.

## 왜 CNN이 필요한가

이미지는 가까운 pixel끼리 강한 관계를 가집니다. 모든 pixel을 fully connected layer에 넣으면 파라미터 수가 너무 많고, 위치가 조금만 바뀌어도 같은 패턴을 다시 학습해야 합니다.

CNN은 이 문제를 다음 방식으로 줄입니다.

- local receptive field: 가까운 영역만 봅니다.
- weight sharing: 같은 filter를 이미지 전체에 반복 적용합니다.
- hierarchical feature: 얕은 layer는 edge, 깊은 layer는 object-level feature를 학습합니다.

## 핵심 구조

```text
Input image
-> Convolution
-> Activation
-> Pooling or Stride
-> Feature map
-> Classifier / Detection head / Segmentation head
```

## Convolution

Convolution은 filter를 이미지 위로 이동시키며 지역 패턴과의 유사도를 계산합니다.

```text
filter가 edge 패턴을 잘 잡으면 edge가 있는 위치에서 큰 activation이 나옵니다.
```

중요한 하이퍼파라미터:

- kernel size: filter 크기
- stride: filter 이동 간격
- padding: 이미지 주변에 값을 덧대는 방식
- channel: feature 종류 수

## Padding

Padding은 이미지 경계 정보가 빨리 사라지는 것을 막거나 출력 크기를 유지하기 위해 사용합니다.

```text
padding 없음: 출력 크기 감소
padding 있음: 경계 영역도 convolution에 참여
```

## Pooling

Pooling은 공간 크기를 줄이고 작은 위치 변화에 더 안정적인 표현을 만듭니다.

- max pooling: 가장 강한 특징을 남김
- average pooling: 평균적인 정보를 남김
- global average pooling: feature map 전체를 하나의 vector로 요약

## CNN의 장점과 한계

장점:

- 이미지의 지역 패턴을 효율적으로 학습합니다.
- 파라미터 수가 fully connected 구조보다 적습니다.
- 작은 데이터에서도 비교적 안정적으로 학습됩니다.

한계:

- 전역 관계를 직접 보기는 어렵습니다.
- receptive field가 넓어지려면 layer를 깊게 쌓아야 합니다.
- 큰 데이터에서는 Transformer 기반 모델이 더 강할 수 있습니다.

## 대표 모델 흐름

| 모델 | 핵심 아이디어 |
|---|---|
| LeNet | 초기 CNN 구조 |
| AlexNet | 큰 CNN으로 ImageNet 성능 개선 |
| VGG | 작은 3x3 convolution을 깊게 쌓음 |
| ResNet | residual connection으로 깊은 모델 학습 |
| EfficientNet | depth, width, resolution을 균형 있게 scaling |

## 면접 포인트

- CNN은 local pattern과 weight sharing이 핵심입니다.
- Padding은 출력 크기와 경계 정보 보존에 영향을 줍니다.
- Pooling은 공간 크기를 줄이고 위치 변화에 대한 안정성을 줍니다.
- ResNet은 깊은 CNN에서 gradient 흐름을 개선하기 위해 residual connection을 사용합니다.
