# Efficient Teacher: Semi-Supervise Object Detection for YOLOv5 / 2023

* alibaba-inc


## Introduction

SSOD(Semi-Supervise Object Detection)의 세 가지 논점

1. One-Stage SSOD의 적은 연구

- 원인 : 

2. Pseudo Label Inconsistency

3. SSOD의 효과적인 



* 참고 설명
1) Anchor-free detector : 일반적으로 사물이 있을만한 위치를 원래 이미지를 pyramid Level에서 각 선별하여 사용하는데, 가판대와 같이 탐지하고자 하는 대상이 긴 경우에는 Anchor-based 방법론이 잘 작동하지 않을 수 있다. 따라서 통상적인 OD에서 사용하는 방법이 아닌 Anchor로 부터 자유로운 모델을 말한다 (ex. FCOS).
