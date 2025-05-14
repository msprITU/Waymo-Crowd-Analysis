# Crowd Analysis on Waymo Dataset
Understanding the location, distribution patterns, and characteristics of crowds—along with the number of objects within a specific space—is a critical field known as crowd analysis. Monitoring and analyzing crowds, especially in urban areas, is vital for applications in security, city management, urban planning, and disaster prevention.
While most existing methods focus on people crowd counting, our work expands this domain by proposing novel approaches for counting and locating vehicles through estimating and generating density maps, and more broadly, counting various objects within road scenes.
To achieve this, we utilized the comprehensive [Waymo Open Dataset](https://waymo.com/open/) and curated a custom sampled subset by manually annotating objects and labeling scenes based on their unique characteristics.
Our work includes a transfer learning-based crowd analysis using single images, and also a more advanced method relying on object flow estimation to count vehicles on video frames and our third approach proposes a method for counting multiple objects within road scenes through training the network with annotated data including multiple object categories.

### 🔍 Project Overview

We propose three complementary approaches for crowd analysis:

### 1. Transfer Learning-Based Vehicle Counting (Single Image)
A convolutional neural network (CNN) trained using transfer learning to estimate the number of vehicles in a **single image**. This approach enables fast and accurate crowd density estimation from static frames. [See details](#crowd-analysis-by-transfer-learning)

### 2. Object Flow Estimation (Video-Based Counting)
A more advanced method that estimates **dynamic object flow** between video frames to track and count vehicles over time, capturing temporal dependencies and motion patterns. [See details](#flow-estimation-based-crowd-analysis)

### 3. Multi-Class Object Counting
A novel approach that counts **multiple object types** (e.g., vehicles, pedestrians, bicycles) within a road scene in video frames. The model is trained using our **manually annotated data** containing various object categories. [See details](#multi-category-crowd-analysis)


### 📦 What’s Included

- ✅ Trained models  
- 📊 Sample outputs and density maps    
- 📋 Data, Annotation and Labeling details 
- 🛠️ Instructions


## Crowd Analysis by Transfer Learning
In this method we employ the [CSRnet network](https://github.com/leeyeehoo/CSRNet), originally developed for people crowd counting and adapted this network to the area of vehicle crowd counting using [Waymo](https://waymo.com/open/) and [TRANCOS](https://waymo.com/open/) datasets. To improve the network performance, transfer-leraning-based Waymo models are trained using pretrained models trained on datasets such as ShanghaiTech and TRANCOS. Our work is presented in our paper titled ["Vehicle Crowd Analysis via Transfer Learning"](https://ieeexplore.ieee.org/document/10382876) at the 30th ICECS 2023 conference.

### Trained Model Files
You can access our trained model files here.
<!---[https://raw.githubusercontent.com/msprITU/Waymo-Crowd-Analysis/main/icecs2023.pdf]--->
|Network|Trained On|Pretrained On|Epoch|Link|
|-------|----------|-------------|-----|----|
|CSRNet|TRANCOS|-       |727|[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/TRANCOS/CSRNetOnlyTrancos727.pth.tar)|
|CSRNet|TRANCOS|ShangT A|99 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/TRANCOS/CSRNetShanghaiATrancos99.pth.tar)|
|CSRNet|TRANCOS|ShangT B|75 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/TRANCOS/CSRNetShanghaiBTrancos75.pth.tar)|
|CSRNet|Waymo  |-       |25 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/Waymo/CSRNetOnlyWaymo25.pth.tar)|
|CSRNet|Waymo  |ShangT A|30 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/Waymo/CSRNetShanghaiAWaymo30.pth.tar)|
|CSRNet|Waymo  |ShangT B|30 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/Waymo/CSRNetShanghaiBWaymo30.pth.tar)|
|CSRNet|Waymo  |TRANCOS |27 |[Download](https://github.com/msprITU/Waymo-Crowd-Analysis/releases/download/Waymo/CSRNetTrancosWaymo27.pth.tar)|
#### Visual Comparison
Visual comparison of ground truth density maps with predicted density maps of OnlyWaymo25 and transfer learning applied TrancosWaymo27 models under different weather conditions
#### Sunny
![segment-1208303279778032257_1360_000_1380_000_with_camera_labels](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/04483e1c-1559-4790-9be5-51239d57ffeb)
![segment-11799592541704458019_9828_750_9848_750_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/0a06daf6-9ad4-4496-82ba-931079fda5ab)
#### Foggy
![segment-11355519273066561009_5323_000_5343_000_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/42b5de6c-accf-4cbf-9536-bc085234ac63)
#### Dark
![segment-14753089714893635383_873_600_893_600_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/2ac76700-de90-42a4-a75f-87397b36a410)

## Flow Estimation-based Crowd Analysis

## Multi-Category Crowd Analysis

