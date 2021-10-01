---
title:  "[ML] NetVLAD Paper One-page Summary"
excerpt: "Let's overview NetVLAD paper with one page summary"

categories:
  - ML
tags:
  - CV

comments: true
last_modified_at: 2021-10-01T00:00:00-23:59
---

# 1. Abstraction

  Visual localization is one of the popular research themes because of its applicability. Especially image retrieval is that we can easily imagine the usual application like image search in google, personal photo grouping, and so on. Thus I want to introduce a breakthrough paper that is NetVLAD in this area.



# 2. Contribution

  The model architecture is closely related to its contributions. So I'll explain it with the contributions.

## *a) Learnable CNN network for vector representation*

![RA5_NetVLAD_Jinyoung Kim(20155052) 2021-10-01 23-01-06](https://user-images.githubusercontent.com/60743304/135633338-29e88697-67ac-42cb-b24a-9ed3b93452f4.png)

  The left figure is the original state-of-the-art architecture VLAD. And the right figure is the model architecture of this paper. What is the difference?

  As we can see in both figures, the difference is that it is implemented in a computational or deep neural network manner. Because the author thinks that the best architecture for image retrieval is that the original state-of-the-art architecture, that is VLAD. But they implement it with CNN based architecture. Let check how can do that.

  Firstly, they replace SIFT feature extractor with pre-trained CNN baseline architecture without the pooling layer (It will do that in the NetVLAD layer). 

  Secondly, they replace the original VLAD as the NetVLAD layer. But original VLAD is not differentiable because it is a hard-assignment(definition of ak(xi) function). So they adopt soft-max for differentiating it! As seen in the left figure, using extracted features from CNN, the model constructs soft-assignment.

## *b) Weakly supervised ranking loss*

![image-20211001230507429](/Users/jin/Library/Application Support/typora-user-images/image-20211001230507429.png)

  How can build a loss term with it? As seen in the left equation, Commonsensicically potential positive data with input data are should closer than negative data. So the inequality is satisfied. Using this truth we can construct loss term like the right figure. With this loss formulation, the model can be trained end-to-end manner with google street view time machine dataset.

## *c) Time Machine Dataset(Google Street View)*

![image-20211001230531968](/Users/jin/Library/Application Support/typora-user-images/image-20211001230531968.png)

  The trained model with only a particular time street view is a week from overfitting and affected by a trivial element like the trees, parked car, and so on. 

  Because, As seen in the left figure, the street view differs from time to time by the fact like light condition, parked car, pedestrians, and so on. 

  Therefore, with a time machine view dataset, the model can be trained robustly from a negative fact.



# 3. Result

![image-20211001230549138](/Users/jin/Library/Application Support/typora-user-images/image-20211001230549138.png)

  As you can check from the left figure, the NetVLAD architecture(magenta) show greater performance than the original state of the art architectures. 

  They prove that nowadays the trainable CNN model is the most powerful image retrieval approach.



<small>All credit by Relja Arandjelovic et al., “NetVLAD: CNN architecture for weakly supervised place recognition”., CVPR 2016</small>
