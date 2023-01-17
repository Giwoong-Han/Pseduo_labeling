# Pseduo_labeling / NIPs 2020


## Short Review

1. Consistency Training이 필요한 이유 -> 많은 양의 Unlabeled Data에 포함된 noise에 영향을 받은 Prediction을 최대한 줄이려고
2. 저자는 두 가지 Type의 Noise를 적용한 Augmentated Data를 Consistency Training에 활용하여 성능을 높히는 기법을 소개합니다.

* Simple Noise : Random Augmentation, Back-translation
* Typical Noise : Additive Gaussian Noise, Dropout Noise, Adverserial Noise

3. Vision과 NLP 둘 다 실험 -> 필자는 Vision에 초점을 두어 설명합니다.

## Methods

- Unsupervised Data Augmentation (UDA)

> * Augmentation의 관점
D(p_($/theta$)(y | x) || p_($/theta$)(y | x, e))
