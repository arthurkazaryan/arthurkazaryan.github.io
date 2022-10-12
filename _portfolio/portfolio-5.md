---
title: "Human Pose Classification"
excerpt: "Detecting the human position on the photo.<br/><img src='/images/portfolio/human_pose_classification/main-500x300.jpg'>"
collection: portfolio
---

<a href="https://github.com/arthurkazaryan/human_pose_classification" title="GitHub">GitHub Repo</a>

# Overview
The dataset contains pictures from an online clothing store with people pictured from different sides - front, side and back. There are two goals to solve:

* classify the side from which the picture was taken;
* classify whether the picture contains full height of a human or not.

<p align="center"><img width="500" src="/images/portfolio/human_pose_classification/overview.jpg"></p>
<p align="center">Samples from archive</p>

# Solution
To solve the problem I've chosen to use <a href="https://google.github.io/mediapipe/solutions/pose.html" title="Mediapipe">Mediapipe Pose Landmark Model</a> tool for computer vision. 
It allows to extract landmark points and, by processing them, classify human standing position.


It is safe to say that if the points on the head and on both feet (from 1 to 10 AND from 27 to 32) are found on the picture, the human is pictured full height. 
Therefore, when predicting, the algorithm will add all the visibility coefficients of that points in a list, and if the mean value is greater than 0.9, the human is pictured in full height. 
<p align="center"><img width="500" src="/images/portfolio/human_pose_classification/height_comparsion.jpg"></p>
Thankfully, the Mediapipe Pose Landmark Model sets a coordinates for each point in 3D, so by extracting them from each picture I can create a dataset to train a classification model.

# Result
The script sends a landmark points into a neural network to predict whether it is a front, side, or back view.
Also, using algorithm, it decides whether it is a full height human, or not.
<p align="center"><img width="500" src="/images/portfolio/human_pose_classification/algorithm.jpg"></p>
