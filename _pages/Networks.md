---
permalink: /networks/
title: "Networks"
author_profile: true
---

<p float="middle">
    <video autoplay="autoplay" src="../images/twon10h_website_labled.mp4" controls="controls" width="100%" />
</p>


## Overview
We design a real-time dense local semantic mapping algorithm, MotionSC as a benchmark on the CarlaSC dataset. We compare with open source state-of-the-art semantic scene completion networks [SSCNet](http://sscnet.cs.princeton.edu/), SSCNet-Full, [LMSCNet](https://arxiv.org/abs/2008.10559) and [JS3CNet](https://github.com/yanx27/JS3C-Net). You can find our implementations of each network on our [GitHub](https://github.com/UMich-CURLY/3DMapping), where we use open source implementations from the authors of the aforementioned papers. The video above shows a comparison of our lightweight model MotionSC with the baselines. 

## MotionSC
MotionSC is built upon the insight that semantic scene completion (SSC) is a fundamentally similar task to mapping. Whereas semantic segmentation is a task which labels merely points that have been directly observed, SSC attempts to complete the scene, similar to what would be desired from a world model. In robotics applications, we desire a complete world model which incorporates all past sensory information. Therefore, we extend SSC to include memory through a temporal axis. 

Our approach builds upon a view-volume network structure, where 3D operations are implicitly performed in 2D for efficiency. We incorporate temporal information through temporal pooling layers and spatio-temporal convolution layers from [MotionNet](https://arxiv.org/abs/2003.06754). A diagram of our network is shown below, and consists of a Spatio-Temporal Pyramid Network backbone with a semantic scene completion head which lifts the dimensionality of the output. The input to the network is a stack of consecutive (temporally) occupancy grids, which may be maintained without significant additional computational overhead. We require that point clouds are transformed to the pose of the current frame, as the network was unable to implicitly learn to transform point clouds in its current form. 

<p float="middle">
  <img src="../images/MotionSC.png" width="100%" /> 
</p>

The layers of the network can be seen in the graphic below. Each Conv2D operation is followed by a BatchNorm2D and ReLU operation. The parameters of each convolution operation are the number of filters f, kernel size, stride, and padding. Any stride 2 operation reduces the H and W dimensions by half, while stride 1 operations preserve dimensions. Unless otherwise specified, dilation (dil) is 1. The ASPP block sums three 3D convolutions with dilations [1, 2, 3] and paddings of [1, 2, 3]. Note that the spatio-temporal convolution operation decreases the size of the temporal axis. For small temporal dimensions rendering the convolution invalid, we replace the 3D filter size with size (1, 1, 1), effectively becoming a fully connected layer. This modification also enables a temporal ablation study, and fair comparison with scene completion networks by setting the size of the temporal axis (T) to 1. 


<p float="middle" class="NETWORKS-image">
  <img src="../images/NetworkVisualization.png"/>
</p>

We performed an ablation study of the effect of the size of the temporal axis (T) and the results are shown in the table below. MotionSC with T = 1 achieves both a higher semantic accuracy and mean intersection over union (mIoU) than the baselines. We observed that as the temporal stack height increases, MotionSC improves at nearly all metrics, most evident by the mIoU scores.
<p align="center">
  <img src="../images/Geometric_Completeness.png" width="100%" /> 

</p>

## Training Logs
We also use the [TensorBoard](https://www.tensorflow.org/tensorboard) to record the training process. You can check how to use the TensorBoard [here](https://pytorch.org/tutorials/recipes/recipes/tensorboard_with_pytorch.html). You can access and download the logs on our [GitHub](https://github.com/UMich-CURLY/3DMapping). The frozen weights for each model may also be found on our GitHub. 

<!-- ## Visualization -->
