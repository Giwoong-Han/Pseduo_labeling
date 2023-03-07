# Efficient Teacher: Semi-Supervise Object Detection for YOLOv5 / 2023

* alibaba-inc


## Introduction

SSOD(Semi-Supervise Object Detection)의 세 가지 논점

1. One-Stage SSOD의 적은 연구

- 원인 : One-Stage에서는 일반적으로 Anchor based detector를 사용하는데, Positive와 Negative Sample이 Imbalance -> 낮은 퀄리티의 Pseudo Labels
- 제안 : Pseudo Label Assigner(PLA) 사용


2. Pseudo Label Inconsistency

- 원인 : Two Stage Model에서는 좀 더 정제된 Pseudo Label을 Student 모델에 학습할 수 있으나, One Stage에서는 쉽지 않음.


3. 높은 정확도와 효율성을 추구하는 요즘 OD 결과

- 원인 : 다양한 현실 문제에 적용하는 입장에서 넓은 시나리오를 제공해 주지 못함.



## 참고 설명

1) Anchor-free detector : 일반적으로 사물이 있을만한 위치를 원래 이미지를 pyramid Level에서 각 선별하여 사용하는데, 가판대와 같이 탐지하고자 하는 대상이 긴 경우에는 Anchor-based 방법론이 잘 작동하지 않을 수 있다. 따라서 통상적인 OD에서 사용하는 방법이 아닌 Anchor로 부터 자유로운 모델을 말한다 (ex. FCOS).

2) Positive & Negative Sample Imbalance : 
① 대부분의 locations은 학습에 쓸모가 없는 배경이기 때문에 학습이 비효율적임
② 배경이 학습에 영향을 줘서, object를 검출하지 못하거나 배경으로 검출하는 오검출을 야기함
