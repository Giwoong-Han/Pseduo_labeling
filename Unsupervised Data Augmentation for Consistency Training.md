# Pseduo_labeling / NIPs 2020


## Short Review

1. Consistency Training이 필요한 이유 → 많은 양의 Unlabeled Data에 포함된 noise에 영향을 받은 Prediction을 최대한 줄이려고
2. 저자는 두 가지 Type의 Noise를 적용한 Augmentated Data를 Consistency Training에 활용하여 성능을 높히는 기법을 소개한다.

* Simple Noise : Random Augmentation, Back-translation
* Typical Noise : Additive Gaussian Noise, Dropout Noise, Adverserial Noise

3. Vision과 NLP 둘 다 실험 → 필자는 Vision에 초점을 두어 설명한다.

## Methods

- Unsupervised Data Augmentation (UDA)

> * Augmentation의 관점
D(p_(Θ)(y|x) || p_(Θ)(y|x, e)) : Augmentation Data와 기존 Data의 분포는 최대한 같아야 한다.
→ 학습의 관점에서는 Noise가 추가된 부분이 Hidden Layer에서 오는 변화가 매우 부드러워야 한다.
→ 다른 관점에서 보면 Labeled Dataset의 정보를 Unlabeled에 Gradually Propagation.
→ 즉, 어느 정도의 Noise를 포함한 이미지를 Unlabeled에 포함시켰을 때 최적의 성능을 줄 수 있는가? (Augmentation보다 Unlabeled를 잘 활용해야한다.)

