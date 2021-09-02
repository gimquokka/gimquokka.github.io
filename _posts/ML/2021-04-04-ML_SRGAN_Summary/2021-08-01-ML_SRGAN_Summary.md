---
title:  "[ML] SRGAN one page summary"
excerpt: "I introduce SR-GAN brifely with one page summary"

categories:
  - ML 
tags:
  - CV
  - GAN

comments: true
last_modified_at: 2021-08-01T22:00:00-00:00
toc: true
toc_sticky: true
---

# 1. Problem

As time goes by, the quantitative measurement like MSE, PSNR in single-image super-resolution is improved by the breakthrough of CNN based deep neural network. Even though It is still hard  to get **finer texture details** at large upscaled SR images. Because there are some limitations of earlier approaches. By presenting SRGAN, the authors try to solve its problem.

![](Aspose.Words.bc55961b-dd70-4365-86f3-f13febbb925b.002.jpeg)Figure 1: MSE loss tends to minimize loss by averaging of a possible solution. It hard to match finer texture details in existing CNN based network. But as seen in the figure, GAN generates one of possible solution **distribution**. It’s easy to get finer texture detail even in large- scaled SR images.



# 2. Solution

It is the main contribution of this paper to introduce **the perceptual loss function** with GAN.

![](Aspose.Words.bc55961b-dd70-4365-86f3-f13febbb925b.003.jpeg)

Equation 1: It is the loss function of GAN. Both of the terms, that content loss, and adversarial loss use perceptual loss that is calculate loss with **feature map** extracted from VGG net, not a point pixel result value. By considering two-term at once, It can get an SR image that has finer texture detail.

![](Aspose.Words.bc55961b-dd70-4365-86f3-f13febbb925b.004.jpeg)

Equation 2: Content loss used for preventing **arbitrary generation result** by calculating loss LR image from generator and HR image.

![](Aspose.Words.bc55961b-dd70-4365-86f3-f13febbb925b.005.jpeg)

Equation3: It’s a common GAN loss. log(1-D) is original form, but usually it’s written -log(D). Because It is easy to train.



 ![](Aspose.Words.bc55961b-dd70-4365-86f3-f13febbb925b.006.jpeg)



# 3. Result

Figure 2: Compare with the others, it seems like SRGAN  gives us a much sharp HR image that has a marginally high MOS value. Nonetheless, SRResNet has high PSNR and SSIM. The reason is that,  As  I  mark in the image,  GAN gives us a noise result that is not the same as the original image. It is one of the characteristics of GAN model. The reason is that learn the distribution of data, and **generate** a result. So, there is a hardship to constrain generation.



# 4. Opinion

The loss is a super important factor in model training. SRGAN uses perceptual loss. It means that the feature map extracted from the network is super important. What if using a more advanced network than VGG net?





_All credit by Ledig et al., “Photo-Realistic Single Image Super Resolution Using a Generative Adversarial Network”., CVPR 2017_
