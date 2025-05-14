# Crowd Analysis on Waymo Dataset
Understanding the location, distribution patterns, and characteristics of crowds—along with the number of objects within a specific space—is a critical field known as crowd analysis. Monitoring and analyzing crowds, especially in urban areas, is vital for applications in security, city management, urban planning, and disaster prevention.
While most existing methods focus on people crowd counting, our work expands this domain by proposing novel approaches for counting and locating vehicles through estimating and generating density maps, and more broadly, counting various objects within road scenes.
To achieve this, we utilized the comprehensive [Waymo Open Dataset](https://waymo.com/open/) and curated a custom sampled subset by manually annotating objects and labeling scenes based on their unique characteristics.
Our work includes a transfer learning-based crowd analysis using single images, and also a more advanced method relying on object flow estimation to count vehicles on video frames and our third approach proposes a method for counting multiple objects within road scenes through training the network with annotated data including multiple object categories.

### 🔍 Project Overview

We propose three complementary approaches for crowd analysis:

### 1. Crowd Analysis by Transfer Learning (Single Image)
A convolutional neural network (CNN) trained using transfer learning to estimate the number of vehicles in a **single image**. This approach enables fast and accurate crowd density estimation from static frames. [See details](#crowd-analysis-by-transfer-learning)

### 2. Flow Estimation-based Crowd Analysis (Video-Based Counting)
A more advanced method that estimates **dynamic object flow** between video frames to track and count vehicles over time, capturing temporal dependencies and motion patterns. [See details](#flow-estimation-based-crowd-analysis)

### 3. Multi-Category Crowd Analysis
A novel approach that counts **multiple object types** (e.g., vehicles, pedestrians, bicycles) within a road scene in video frames. The model is trained using our **manually annotated data** containing various object categories. [See details](#multi-category-crowd-analysis)


### 📦 What’s Included

- ✅ Trained models  
- 📊 Sample outputs and density maps    
- 📋 Data, Annotation and Labeling details 
- 🛠️ Instructions


### Labled Scene Attributes
![Labled Scene Attributes](https://github.com/user-attachments/assets/04151b55-d8fb-4eca-aba6-f6a7eaef0b5a)



## Crowd Analysis by Transfer Learning
In this method we employ the [CSRnet network](https://github.com/leeyeehoo/CSRNet), originally developed for people crowd counting and adapted this network to the area of vehicle crowd counting using [Waymo](https://waymo.com/open/) and [TRANCOS](https://waymo.com/open/) datasets. To improve the network performance, transfer-leraning-based Waymo models are trained using pretrained models trained on datasets such as [ShanghaiTech](https://github.com/desenzhou/ShanghaiTechDataset) and TRANCOS. Our work is detailed in our paper titled ["Vehicle Crowd Analysis via Transfer Learning"](https://ieeexplore.ieee.org/document/10382876) as presented in the 30th ICECS 2023 conference.

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
#### Sample outputs
Visual comparison of ground truth density maps with predicted density maps of OnlyWaymo25 and transfer learning applied TrancosWaymo27 models under different weather conditions
#### Bright scene
![segment-1208303279778032257_1360_000_1380_000_with_camera_labels](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/04483e1c-1559-4790-9be5-51239d57ffeb)
![segment-11799592541704458019_9828_750_9848_750_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/0a06daf6-9ad4-4496-82ba-931079fda5ab)
#### Blurry Scene
![segment-11355519273066561009_5323_000_5343_000_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/42b5de6c-accf-4cbf-9536-bc085234ac63)
#### Dark Scene
![segment-14753089714893635383_873_600_893_600_with_camera_labels tfrecord](https://github.com/msprITU/Waymo-Crowd-Analysis/assets/56837349/2ac76700-de90-42a4-a75f-87397b36a410)

## Flow Estimation-based Crowd Analysis

## Multi-Category Crowd Analysis





### Data details
Here is a detailed list of segments used for training and testing along with information about scene characteristics (attributes) and object instances.
<div style="overflow-x: auto; font-size: 12px;">
  
| Segment ID | Bright | Dark | Overcast | Occlusion | Low Density | Blurry | Pose | Scale | # Vehicles | # Pedestrians | # Bicycles |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 102353 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6781 | 218 | 26 |
| 100822 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 2799 | 539 |  |
| 104444 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 5047 | 2750 | 89 |
| 100508 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2799 | 272 |  |
| 102261 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 4239 | 1546 |  |
| 102319 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 6072 | 1912 | 40 |
| 104859 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 5210 | 6546 | 83 |
| 108768 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 3709 | 632 |  |
| 109277 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 7326 | 600 |  |
| 106762 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2445 | 44 | 23 |
| 112193 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 3019 | 37 |  |
| 111130 | ✓ |  |  |  | ✓ |  |  | ✓ | 1330 | 6927 | 198 |
| 116741 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6248 | 2586 | 144 |
| 123218 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4854 | 4870 |  |
| 121797 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2193 | 136 |  |
| 123049 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 5124 |  |  |
| 125050 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 8486 | 3598 | 194 |
| 123392 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 8147 | 5347 | 94 |
| 128485 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 8265 |  |  |
| 129008 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 3054 |  |  |
| 131967 | ✓ |  |  | ✓ | ✓ |  | ✓ | ✓ | 591 |  |  |
| 128966 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4532 | 6422 | 170 |
| 132544 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 5297 | 4207 |  |
| 134763 |  |  | ✓ |  | ✓ |  | ✓ | ✓ | 870 |  |  |
| 135064 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6955 | 961 | 111 |
| 132384 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 3389 | 301 |  |
| 134024 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 4237 | 6250 |  |
| 138305 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 4201 |  |  |
| 139407 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 2058 |  |  |
| 142292 | ✓ |  |  | ✓ | ✓ |  | ✓ | ✓ | 854 | 118 | 94 |
| 141339 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 5220 | 2337 | 84 |
| 141184 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6006 | 604 | 75 |
| 138401 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 7000 | 2531 | 919 |
| 140185 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4316 | 844 |  |
| 141430 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 3876 | 1192 | 511 |
| 141837 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 11798 | 1547 | 191 |
| 142505 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 5001 | 22 |  |
| 143481 |  |  | ✓ |  | ✓ | ✓ | ✓ | ✓ | 1076 |  |  |
| 147427 |  |  | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | 1910 |  |  |
| 142761 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 439 | 207 | 151 |
| 145617 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 5119 | 64 |  |
| 144793 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 4006 |  |  |
| 147348 |  | ✓ |  |  | ✓ |  | ✓ | ✓ | 1232 |  |  |
| 148106 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4562 | 4774 |  |
| 143692 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 1208 | 480 |  |
| 148188 |  |  |  | ✓ | ✓ |  | ✓ | ✓ | 10092 | 2209 | 100 |
| 152664 |  |  |  | ✓ | ✓ |  | ✓ | ✓ | 4594 | 8719 | 483 |
| 152021 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 9788 | 2006 |  |
| 151664 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 2083 | 101 |  |
| 153086 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 3886 | 87 |  |
| 153495 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 1184 | 156 |  |
| 149641 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 7241 | 1291 |  |
| 148697 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 3382 | 91 |  |
| 153677 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 2910 |  |  |
| 148300 | ✓ |  |  | ✓ | ✓ |  | ✓ | ✓ | 2521 | 191 | 199 |
| 149401 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 7463 | 738 |  |
| 153428 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 3973 |  |  |
| 153318 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6464 | 5235 |  |
| 158445 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4290 | 1863 | 432 |
| 153793 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 3969 | 2146 |  |
| 156969 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 5834 | 160 | 149 |
| 155334 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 6099 | 1275 | 25 |
| 158823 | ✓ |  |  | ✓ |  | ✓ | ✓ | ✓ | 5212 | 3660 | 245 |
| 157877 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2073 | 585 | 109 |
| 158573 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 3957 | 1142 |  |
| 155350 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 5547 | 3105 | 241 |
| 154484 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 6494 | 3394 |  |
| 156289 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 8799 | 571 | 216 |
| 158686 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2817 | 24 |  |
| 161022 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 7883 | 195 |  |
| 159035 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 368 | 95 |  |
| 166004 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 3026 | 5426 |  |
| 165612 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 5270 | 3207 | 106 |
| 166766 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 3975 |  |  |
| 167359 | ✓ |  |  | ✓ | ✓ | ✓ | ✓ | ✓ | 666 | 124 | 55 |
| 166526 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 2487 | 487 | 44 |
| 165342 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 3776 | 597 |  |
| 102252 | ✓ |  |  |  |  |  | ✓ | ✓ | 4915 | 1790 |  |
| 107239 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 6277 | 1775 |  |
| 110708 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 5359 | 7395 |  |
| 113189 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6600 | 2337 | 34 |
| 100239 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 4462 | 3871 | 31 |
| 102124 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 3824 | 751 |  |
| 104554 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 6645 | 711 |  |
| 108305 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 3696 | 106 |  |
| 109636 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 5923 | 872 |  |
| 112365 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 5978 | 6897 | 68 |
| 112520 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 2126 | 5707 |  |
| 125818 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6647 | 644 |  |
| 141665 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ |  |  |  |
| 138622 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 4842 | 4276 | 6 |
| 140734 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 1991 |  |  |
| 139654 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 658 | 11 | 175 |
| 140185 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 4316 | 844 |  |
| 140735 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 4263 |  |  |
| 141930 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 2186 |  | 56 |
| 142335 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 8825 | 608 |  |
| 140760 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6986 | 1793 |  |
| 140045 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 1 | 1 | 1 |
| 145031 | ✓ |  |  | ✓ | ✓ |  | ✓ | ✓ | 574 | 84 |  |
| 144248 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 2398 | 82 |  |
| 144309 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 2986 | 119 |  |
| 143882 | ✓ |  |  |  | ✓ |  | ✓ | ✓ | 225 | 76 |  |
| 143581 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 1861 | 88 |  |
| 143291 |  |  | ✓ |  | ✓ |  | ✓ | ✓ | 2120 | 225 |  |
| 147523 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 2411 | 160 |  |
| 147637 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6585 | 263 |  |
| 147663 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 2329 | 616 |  |
| 147368 |  | ✓ |  | ✓ |  |  | ✓ | ✓ | 4204 | 259 |  |
| 147912 | ✓ |  |  |  | ✓ | ✓ | ✓ | ✓ | 1714 | 392 |  |
| 154820 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 920 | 1899 |  |
| 158343 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6542 | 1090 |  |
| 155786 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 6569 | 580 |  |
| 155506 | ✓ |  |  | ✓ |  |  | ✓ | ✓ | 2237 | 264 |  |
| 157178 | ✓ |  |  | ✓ | ✓ |  | ✓ | ✓ | 894 | 21 |  |
| 155396 |  |  | ✓ | ✓ |  | ✓ | ✓ | ✓ | 5173 | 362 |  |
| 156465 |  |  | ✓ | ✓ |  |  | ✓ | ✓ | 6564 | 5684 |  |

</div>
​
