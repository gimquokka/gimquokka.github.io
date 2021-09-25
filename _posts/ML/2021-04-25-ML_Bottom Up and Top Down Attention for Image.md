---
title:  "[ML] 'Bottom Up and Top Down Attention for Image' Paper One-page Summary"
excerpt: "Let's overview 'Bottom Up and Top Down Attention for Image' paper with one page summary"

categories:
  - ML
tags:
  - CV

comments: true
last_modified_at: 2021-09-25T00:00:00-23:59
---



# 1. Abstraction

![그림1](https://user-images.githubusercontent.com/60743304/134773670-d8b6640d-deee-4dd5-982d-916795b3a652.png)

Image capture and VQA encompass both CV and NLP. The top-down approach *left side of figure* is mainly used for the CV task of it. But as we can see that intuitively there is a limitation of a top-down approach that it just treats the image in a grid-wise way not object-wise. 

So if we use a properly bottom-up approach(*right side of figure*), the model can understand and utilized image information for the tasks. This paper covers how to improve image captioning and VQA performance with the combination of top- down and bottom-up manner. 

# 2. Structure

 a) *Bottom -Up Attention Model*

![그림1](https://user-images.githubusercontent.com/60743304/134773685-4ab02d0c-9f14-4f21-b6d2-0a7b64a7275c.png)

 In this paper, they use Faster R-CNN is a Bottom-up way for combining with the top- down one. The model uses Resnet-101 as a pre-trained model. With the Faster R-CNN, It sets the region and labels to detect the object from a given image. And they add “Attribute Pre-Dictor” to Faster R-CNN for predicting object class in the candidate area better. The given bottom-up mechanism is combined with a different top-down one to carry out image captioning and VQA. 



b) *Captioning Model*

<img width=150 src="https://user-images.githubusercontent.com/60743304/134773707-d7bcda16-441a-4198-8ab1-e00ee47d03d8.png" alt="그림1" style="zoom:200%;" />



 The capturing model uses LSTM that is utilizing output partial sequence as a context. soft top-down orientation is used to calculate the feature weight for each caption generation. 

`  `It consists of two layers of LSTM and each layer is responsible for different parts. The first layer is the Top-Down assertion LSTM layer which is inputted to the previous language LSTM, the mean pooling value of the image, words previously generated. The final output y\_t is a series of words from Language LSTM, and the final output statement is determined by multiplying the conditional distribution at each time point.



c) *VQA Model* 

![그림1](https://user-images.githubusercontent.com/60743304/134773721-1bcba57e-2f77-4b69-8090-d29dc78c509b.png)

In VQA models, the question is used as a context, and just like on the VQA model, soft attention is used.  

And It is a joint multi-modal embedding structure that uses both images and questions for the task. When creating an image feature using the question and lastly calculate the predicted score about the candidate answers with the question and image feature concatenation. 



# 3. Conclusion



<img width=200 src="https://user-images.githubusercontent.com/60743304/134773742-10dd49d6-2284-4923-9db1-5b8f3b858d92.png" alt="그림1" style="zoom:200%;" />



<img width=400 src="https://user-images.githubusercontent.com/60743304/134773767-e1ec56af-abc2-4244-9e22-869dd8b94e34.png" alt="그림1" style="zoom:200%;" />

<img width=400 src="https://user-images.githubusercontent.com/60743304/134773808-2db5bae9-b89d-4876-b7d6-02b2be6de5ed.png" alt="그림1" style="zoom:200%;" />

  The experiment was carried out using “MS-COCO” and “VQA v2.0” datasets and, as expected, shows better performance than the existing ones. And also the model has a good understanding of the image from a quantitative analysis point of view.



<small>All credit by Anderson et al., “Bottom-Up and Top-Down Attention for Image Captioning and VQA”., CVPR 2018</small>

