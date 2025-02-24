---
permalink: /dataset/
title: "Dataset"
author_profile: true
---


<p float="middle">
    <video autoplay="autoplay" src="../images/web_highres_voxels_quaterspeed.mp4" controls="false" width="100%" />
</p>

Welcome! **CarlaSC** is a semantic scene completion dataset with the aim of increasing scene understanding in dynamic environments. Dynamic environments are challenging for scene understanding because dynamic objects leave behind traces and occlusions in completed scenes. As a result, quantifying performance and supervising training of algorithms from real world data is difficult. Therefore, we propose **CarlaSC**, a synthetic outdoor driving dataset generated from *randomly sampled multi-view geometry*.

## Overview

Our dataset consists of 24 sequences, generated from eight maps with a light traffic, medium traffic, and heavy traffic sequence for each. We obtain data from the [CARLA](https://carla.org/) simulator for its realism, autonomous traffic, and synchronized ground truth. Each sequence consists of three minutes of driving sampled at 10 Hz, for a total of 1800 frames. Each frame contains ground truth data including:

* Observed **point clouds** with **semantic labels** and ego-motion compensated **scene flow** for each point.
* **Pose** and **time** of each observation.
* **Complete semantic scene** represented in Cartesian and Cylindrical coordinates. The scene is obtained from twenty randomly placed LiDAR sensors, placed in new locations for every sequence.
* **Bird's Eye View** image for verification.

## Scan Properties

For every frame in our data set, there is a point cloud with ground truth semantic labels and scene flow vectors, a bird’s eye view image for validation, ground truth pose and time, and ground truth semantically labeled scenes. We offer ground truth scenes in both cylindrical and cartesian coordinates, but primarily focus upon the cartesian system. Scenes are available in two resolutions, one of size 128x128x8 and the other of size 256x256x16. We include not only the region directly ahead of the ego vehicle in our semantically labeled scenes, but the full surroundings of the ego vehicle as we believe the entire scene is important for safe navigation and planning. 


The exact dimensions for each scene in cartesian and cylindrical coordinates is shown below.

<p float="middle">
  <img src="../images/CarlaSCGrid.png" width="100%" />
</p>

Our multi-view scenes include free space labels and minimal occlusions. Each map divided into a low traffic, medium traffic, and high traffic setting. Low traffic is defined as 25 autonomous pedestrians and vehicles, medium traffic as 50 of each, and high traffic as 100. An example image from our dataset compared to a similar frame in the well-known [Semantic KITTI](http://www.semantic-kitti.org/) dataset is shown below. 

<p float="middle">
  <img src="../images/HD.png" width="51%" />
  <img src="../images/BadKITTIOrig.png" width="45%" />
</p>

## Classes

There are 23 semantic [classes](https://carla.readthedocs.io/en/latest/ref_sensors/#semantic-segmentation-camera) in the CARLA simulator. We remove all unlabeled points, and use class 0 to instead represent free space. We also remove any observations of the ego-vehicle, resulting in a clean dataset. A histogram of the frequency of all classes is shown below. 

<p float="middle">
  <img src="../images/HistogramAll.png" width="75%" /> 
</p>

As can be seen, the distribution of classes is very uneven. Some classes are nearly identical to others, and some classes such as sky do not show up at all. Therefore, we also propose a remapping of the classes to aid with training supervised learning algorithms.

<p float="middle">
  <img src="../images/ClassRemapping.png" width="65%" />
</p>
<p float="middle">
  <img src="../images/HistogramRemapped.png" width="75%" /> 
</p>
  


## Format

Our data set is split into two coordinate systems with three splits each. There is a Cartesian and Cylindrical semantic scene completion data set, each with a training, validation, and testing split. Note that the coordinate system is only modified for the *output semantic scene*, while the coordinate system for point clouds and poses is Cartesian in both. An example of the same scene in both coordinate systems is shown below, with a Bird's Eye View camera image for reference. Cylindrical coordinates represent objects near to the ego vehicle in high resolution while further away objects are granular. Cartesian coordinates maintain a consistent resolution throughout the volume. 

<p align="center">
  <img src="../images/BEV.png" width="30%" />
</p>
<p align="center">
  <img src="../images/Cartesian.png" width="45%" /> 
  <img src="../images/Cylindrical.png" width="45%" /> 
</p>

The file structure of our data is shown below. Formats are similar to that of Semantic KITTI, where semantic labels are stored as a [NumPy](https://numpy.org/) uint32 file with the extension ".label" and other files including point locations, number of points per cell, and scene flow are stored as a [NumPy](https://numpy.org/) float32 file with the ".bin" extension. Files are stored as a six character string indicating the frame number followed by an extension, which may be mapped to an exact time using the "times.txt" file. Note that all files use the ego sensor coordinate frame. 

### Updated Dataset with Fine Resolution (May 25, 2022)

To better match with the standards set by SemanticKitti, we have also provided a separate version of the semantic scene completion ground truth in the same voxel resolution as SemanticKitti. Specifically, the voxel grid for each frame is of size 256x256x16 over the same volume as before. The fine resolution download links can be found in the Download page for the Cartesian dataset. Note: The download links only contain the evaluation directory as all others are unaffected by voxel resolution and can be downloaded from the original Cartesian dataset.

<p align="left">
  <img src="../images/Folder.png" width="35px" />
   <b>Split</b> (Train, Val, and Test)
</p>

<p align="left" style="text-indent: 50px;">
  <img src="../images/Folder.png" width="35px" />
   <b>Sequence</b> 
</p>

<p align="left" style="text-indent: 100px;">
  <img src="../images/Folder.png" width="35px" />
   <b>Coordinates</b> (cartesian or cylindrical)
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Folder.png" width="35px" />
   <b>bev</b> bird's eye view image of each frame
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Folder.png" width="35px" />
   <b>evaluation</b> semantic scene completion ground truth
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Folder.png" width="35px" />
   <b>labels</b> semantically labeled point cloud for each frame
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Folder.png" width="35px" />
   <b>predictions</b> ego-motion compensated scene flow for each frame
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Folder.png" width="35px" />
   <b>velodyne</b> raw point cloud without intensity
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Paper.png" width="35px" />
   <b>poses.txt</b> 
</p>

<p align="left" style="text-indent: 150px;">
  <img src="../images/Paper.png" width="35px" />
   <b>times.txt</b> 
</p>

