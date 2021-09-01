---
title:  "[ML] Flow-Net one page summary"
excerpt: "Overview Flow Net with one page summary"

categories:
  - ML
tags:
  - TIL

comments: true
last_modified_at: 2021-04-19T22:00:00-00:00
---

# 0. Reason for selection

I think this paper is a singular point of the optical flow field. Because It was the first end-to-end network that compares performance to the traditional method. And It has become one of the classic paper in that there are many published network adopt it, as well as high citation number. Thus I will cover this paper as a summarization topic.



# 1. Problem

Original FlowNet was a great breakthrough in that it tried to apply Deep Learning to optical flow, that had been performed handcraft manner method. Even if there is no comparison regard to performance between it and the traditional method like EpicFlow, FlowFields. So, the authors advance FlowNet as FlowNet 2.0 in this paper.



# 2. Contribution

## a) Training data and it’s scheduling important

<img width="325" alt="RA2_Jinyoung Kim(20155052) 2021-09-01 17-29-23" src="https://user-images.githubusercontent.com/60743304/131638857-9f26fb64-8d79-4e91-98f7-4b8996b2e257.png">

It can't help but compare FlowNet1.0 to it's 2.0. In FlowNet 2.0, Flying Things 3D Dataset is additionally used.

And more interesting is that the dataset present scheduling in training is one of the important things in the training model. We can see in the chart that if we first train the model Flying Chairs model and then use the Fly Things3D dataset, the models perform better compared to training with other datasets.

## b) Stacked Architectrue

<img width="676" alt="RA2_Jinyoung Kim(20155052) 2021-09-01 17-31-14" src="https://user-images.githubusercontent.com/60743304/131639500-d251836d-a347-425e-bdbd-2834f7b5bd5f.png">

The first chart is that various trials that stacked structure of marked upper line in the model structure diagram. S and C mean Simple and Correlation version of FlowNet. Small s and c is a downside(3/8) version of it (because of decreasing computational cost). As we can see on the table, C+S+S = CSS combination outweigh than others. I think that It might be reflected a trend of DL model structure that goes larger as time goes by for a high performance

## c) Decrease Noise from Small Displacement

The most Traditional method have hardship for large displacement. Contrastively original FlowNet had a problem for small displacement noise. For improving it, In this paper suggest FlowNet-SD, that is marked lower line of model structure, is that handle small displacement with reducing receptive field by using multiple 3x3 kernels.



# 3. Result

<img width="400" height = "250" alt="RA2_Jinyoung Kim(20155052) 2021-09-01 17-34-39" src="https://user-images.githubusercontent.com/60743304/131639640-62831e3b-e864-4069-8c63-33a9f9316ee1.png">

FlowNet 2.0 has a quite reasonable Average EFE, and Runtime comparing with it's 1.0 and the other handcraft method like FlowField, EpicFlow, and so on. Nevertheless, Runtime is marginally longer than the original FlowNet.



# 4. Limitation

Its runtime is largely slow to use it real-time application. Because It can process about 7 ~8 fps. So, It is needed to decrease computation cost in future work. That's exactly Lite-FlowNet!





*All credit by Eddy Ilg et al., “FlowNet 2.0: Evolution of Optical Flow Estimation with Deep Networks”., CVPR 2017*
