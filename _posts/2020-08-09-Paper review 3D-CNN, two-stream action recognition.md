---
title:  "3D-CNN, two-stream action recognition paper review"
excerpt: "Paper review of "3D-CNN" and "two-stream action recognition"

categories:
  - ML 
tags:
  - CV

comments: true
last_modified_at: 2020-08-09T22:00:00-00:00
---

# Paper

- (1) [Learning Spatiotemporal Features with 3D Convolutional Networks](http://openaccess.thecvf.com/content_iccv_2015/html/Tran_Learning_Spatiotemporal_Features_ICCV_2015_paper.html)
- (2) [Two-stream convolutional networks for action recognition in videos](https://papers.nips.cc/paper/5353-two-stream-convolutional-networks-for-action-recognition-in-videos.pdf)



# Overview

- Still there are so many problem in video understanding as opposed to image recognition
- If model process all frame in video, It’s getting too much computation. Every model sampling frame  for computation efficiency.
- - As a result, It is problem that the models could not recognize action that occur between sampled frame to sampled frame
- In second paper, it does not define how to vectorize frame as optical flow. And there are many way to do it. It is also one of main research topic.
- Actually, 3D-CNN swipe not only for height(H) and vertical(V), that is frame, but also length(L) that is temporal data in video.
  - But What confusing things is that every frame also has RGB value(Character). So virtually 3D-CNN work in 4-dimension(H x W x <C> x L). In figure 1 - (c), dimension C is omitted. Be careful of it!
  - Filter does not swipe in the direction of C. Bcz C of filter match with C of frame
- In modern video understanding model, It is mainstream trend that how to harmonize optical flow and 3D-CNN.
  - As we have seen in transformer, BERT, Attention before, Don’t need RNN model for memorize temporal feature in video understanding. Bcz we can memorize temporal data only with CNN. RNN make computation slow due to impossibleness of parallel process
- Key contribution of each paper is
  - (1) 3D-CNN model
  - (2) Optical flow, It use 2D-CNN



# Question

- What kinds of field use Video descriptor?
  - => Every field use video. Deep learning could be replacement of orignal one
- Two paper key difference is 3D CNN, Optic flow?
  - => YES.
- Modern model use them together? or is there different model that can train end2end model?
  - => Belong to the former
- Stack 2d conv, 3d conv net how It is significantly different? how?
  - C-dimension filter size is different. In 3D-conv, It should match with frame of it. But the opposition is not
- how they work actually? Could u practically explain it?
  - It is same as 2D-CNN model do.
- In case of 3d can, there is no loss of labeling data as oppose to later paper?
  - No, Every model do sampling similarly
- LSTM? Is better for capturing temporal data? Isn’t it?
  - NO. As stated above RNN actually doesn’t good choice bcz of unable to parallelize