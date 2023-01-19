# Unsupervised Data Augmentation for Consistency Training / NIPs 2020

* Google Research, Brain Team


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

##  Discussion

1. Valid Noise
Augmentated Dataset은 동일한 GT를 사용하므로 매우 신중할 필요가 있다. 따라서 Unlabeld Dataset에서 Augmentation 기법을 적용하여 Unlabeled 내에서 Consistency Loss를 Minimize하는 것이 좋다.

2. Diverse Noise
다양하게 Augmentation된 Dataset들의 Consistency를 높히는 것이 학습 입장에는 효과적일 것이다.

3. Targeted inductive biases
다른 테스크는 다른 Inductive Biases를 필요로 한다. 따라서 Data Augmentation이 잘 작용하려면 지도학습 부분에서 놓친 Inductive Biases를 제공해야한다.
