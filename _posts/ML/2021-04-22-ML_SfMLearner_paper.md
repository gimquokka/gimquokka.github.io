---
title:  "[ML] SfMLearner Paper One-page Summary"
excerpt: "Let's overview SfMLearner paper with one page summary"

categories:
  - ML
tags:
  - CV

comments: true
last_modified_at: 2021-10-02T00:00:00-23:59
---

# 1. Abstraction

  When I working in an AI startup, It was one of the biggest hardships and expansive steps that make a labeled dataset for model training. In my experience, the difference between supervised and unsupervised manner is critically different for a real-world situation. So, I want to introduce this paper that firstly introduces the model that simultaneously learn the depth and pose in an unsupervised manner.



# 2. Overall architecture

![image](https://user-images.githubusercontent.com/60743304/135720470-0652f167-bdbd-42a1-9efd-0b1b4f960fd1.png)

  As we can see in the left figure, It consists of an independent single-view depth and pose/explainability network.  

  A single-view depth network gets a single image as input and generates the depth map of it. and It has an encoder-decoder structure.

  pose/explainability network gets a pair of an image as input and makes a two 6 DOF of camera poses and explainability mask. pose and explainability network share feature layer. We will see more detail about the explainability mask later.



# 3. Contribution

## a) Unsupervised Learning

![image](https://user-images.githubusercontent.com/60743304/135720530-6dea1e4c-914a-47a1-8023-730c987e196a.png)

  This network training deep learning model in an unsupervised manner. It means that the network does not label data for the training model. Instead, It uses depth and poses information on a nearby frame (t-1, t, t+1) for training.

## b) Photometric Error

![image](https://user-images.githubusercontent.com/60743304/135722244-0ff69aff-beaf-4d1a-81c7-1bcc33a4d950.png)

  As we can check from the left loss term, the per-pixel photometric loss is properly inter combined with the explainability mask. But What a to be desired in it is that this loss is based on the pixel intensity difference, so it is inherently hard to train a low-texture region and the estimated pixel location is marginally incorrect. 

## c) Explainability Mask

![image](https://user-images.githubusercontent.com/60743304/135722264-709f8dec-6099-46aa-b1b6-e93ceb13822a.png)

  The Explainability mask is that pixels are hard to explainable by the model because of motion, occlusion, visibility, and the others. Because this model uses only a single image to estimate the depth map there is a limitation as mentioned in part b). As loss term part b) and left figure, the photometric loss cooperates with the mask. The mask weighting and regularize loss depends on the pixel is explainable or not. By doing so, during the training, the model can minimize the side effect caused by unexplainable pixels.



# 4. Result

![image](https://user-images.githubusercontent.com/60743304/135722277-cee0d4d9-5c5f-4493-be7b-cddf9226598c.png)

  The author argues that performance is quite comparable with the supervised model. But as we can see in the left figure, the result depth map is too blurred and rough. I think as mentioned in 2 - b), c), this network depends on the pixel intensity-based loss term and has two regularization terms. (I'll deal it more detail in limitation) I guess that, even though this model has some, It is hard to use real-world applications. 

 

# 5. Limitation

  1) It is hard to use an online dataset. because this approach assumes camera intrinsic is given condition. In part 2 - b) "Ps ~ KTt->sDt~" term, K means camera intrinsic.** 

  2) This model will work well only in a sequential frame dataset like KITTI. Because loss term is made to use this frame relation information. Thus It'll hard to generalize in normal application**

  3) In this model there is no exact real-world value like baseline in the stereo depth estimation. thereby It would be really hard to estimate the actual scale of depth. Because It only estimates depth with only a single image.



<small>_All credit by Zhou et al., “Unsupervised Learning of Depth and Ego-Motion from Video”., CVPR 2017_</small>
