# Crowd Analysis on Waymo Dataset
## Crowd Analysis by Transfer Learning
### Trained Model Files
Models trained for the 30th ICECS 2023 conference paper ["Vehicle Crowd Analysis via Transfer Learning"](https://ieeexplore.ieee.org/document/10382876) are available here.
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

### TODO
- The code used for training and testing will be added to the repository.
