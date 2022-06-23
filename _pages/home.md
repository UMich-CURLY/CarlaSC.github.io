---
permalink: /
title: "CarlaSC"
excerpt: "About me"
author_profile: true
redirect_from: /sitemap/
---

<p>A Data Set and Network for Real-Time Semantic Mapping in Dynamic Environments</p>

<p float="middle">
<div>
    <video autoplay="autoplay" src="./images/town10h_wh_4x.mp4" controls="controls" width="100%" />
</div>
</p>

<div class="page__lead">
    <div class="page__content">
        <div class="HOME-feature-block">
            <div>
                Trace Free Scenes
                <p>
                    <img src="./images/TraceFree.png" alt="Trace Free">
                </p>
                <p>
                    CarlaSC scenes are sampled from multiple viewpoints, ensuring minimal occlusions and no traces left by dynamic objects. The image above showcases MotionSC lack of traces for dynamic objects compared to SemanticKITTI, another well known vision benchmark.
                </p>
            </div>
            <div>
                Sequential Labels
                <p>
                    <img src="./images/SemanticLabel.png" alt="SemanticLabel">
                </p>
                <p>
                    Data is captured at 10Hz and semantic labels along with scene flow data ground truth data is provided for each frame. This provides more information for scene understanding over multiple scans.
                </p>
            </div>
            <div>
                Synthetic Data
                <p>
                    <img src="./images/Carla.png" alt="Carla">
                </p>
                <p>
                    CarlaSC is generated using CARLA, an open source simulator for autonomous driving research. This enables high customizability, from the number of dynamic objects to the position and number of sensors.
                </p>
            </div>
            <!-- <p class="small">
                Additional Information here.
            </p> -->
    </div>

</div>

<div class="page__content">
    Getting started
    <p class="small">
        A description of the dataset and its properties can be found in the <a href="./dataset/">Dataset</a> page on this website. To download it, please visit the <a href="./download/">Download</a> page to download the Cartesian or Cylindrical dataset version. An example of how to use the dataset can be found on the <a href="https://github.com/UMich-CURLY/3DMapping">MotionSC Github</a> repository. This repository contains the CarlaSC dataloader used in the MotionSC paper as well as python visualization scripts.
    </p>
</div>  

<div class="page__content">
    <div>
        Paper
    </div>
    <p class="small">
        See our paper below for more information and our network baseline results: 
        <div>
            <img src="./images/MotionSCPaperAll.png" alt="MotionSC Paper Here" background-size="cover">
        </div>
        <p class="small">
            If you plan to use our dataset and tools in your work, we would appreciate it if you could cite our paper.
            (<a href="https://arxiv.org/abs/2203.07060">PDF</a>)
        </p>
    </p>
</div>  

