# Efficient Teacher: Semi-Supervise Object Detection for YOLOv5 / 2023

* alibaba-inc


## Introduction

SSOD (Semi-Supervise Object Detection)의 세 가지 논점

1. One-Stage SSOD의 적은 연구

- 원인 : One-Stage에서는 일반적으로 Anchor based detector를 사용하는데, Positive와 Negative Sample이 Imbalance -> 낮은 퀄리티의 Pseudo Labels
- 제안 : Dense Detector, Epoch Adaptor (EA) 사용


2. Pseudo Label Inconsistency

- 원인 : Two-stage Model에서는 좀 더 정제된 Pseudo Label을 Student 모델에 학습할 수 있으나, One-stage에서는 쉽지 않음.
- 제안 : Pseudo Label Assigner (PLA) 사용


3. 높은 정확도와 효율성을 추구하는 요즘 OD 결과

- 원인 : 다양한 현실 문제에 적용하는 입장에서 넓은 시나리오를 제공해 주지 못함.
- 제안 : SOTA를 찍는 동시에 낮은 FLOPs를 사용

## Contribution

현재 Anchor-free, Two-stage에서는 Semi-supervised의 Pseudo Label에서 발생하는 Inconsistency Problem에 대한 연구가 진행되었으나 (실제로 개선된 성능을 보임), 처음으로 One-stage, Anchor-based 방법론에 적용한 논문임.

## 제안 방법론

### Dense Detector

Dense Detector은 ResNet-50-FPN Backbone기반으로 FPN의 output을 5에서 3으로 변경 및 Detection header들 간의 공유되는 Weight을 제거하면서 Input Resolution을 1330에서 640으로 변경함.

### Pseudo Label Assigner (PLA)

### Epoch Adaptor (EA)

## 참고 설명

1. Anchor-free detector : 일반적으로 사물이 있을만한 위치를 원래 이미지를 pyramid Level에서 각 선별하여 사용하는데, 가판대와 같이 탐지하고자 하는 대상이 긴 경우에는 Anchor-based 방법론이 잘 작동하지 않을 수 있다. 따라서 통상적인 OD에서 사용하는 방법이 아닌 Anchor로 부터 자유로운 모델을 말한다 (ex. FCOS).

2. Positive & Negative Sample Imbalance : 
① 대부분의 locations은 학습에 쓸모가 없는 배경이기 때문에 학습이 비효율적임
② 배경이 학습에 영향을 줘서, object를 검출하지 못하거나 배경으로 검출하는 오검출을 야기함

3. NMS (Non-maximum Suppreisson) :
① 모든 bounding box에 대하여 threshold 이하의 confidence score를 가지는 Bounding Box는 제거
② 남은 Bounding Box들을 Confidence score 기준 모두 내림차순 정렬
③ 맨 앞에 있는 Bounding box 하나를 기준으로 잡고, 다른 bounding box와 IoU 값을 구함. IoU가 threshold 이상인 Bounding box들은 제거
④ 해당 과정을 순차적으로 시행, Confidense threshold가 높을수록, IoU threshold가 낮을수록 더 많은 bounding box가 제거
