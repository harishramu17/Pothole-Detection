Pothole Detection via ResNet50
==============================
![](https://github.com/kavinvengidu/Pothole_Detection_IntelOneAPI/blob/main/Images/image_processing20210905-7828-1qbj62x.gif)

This whole Project was primarly build for the **__Intel OneAPI competition 2023
Pothole Detection__**

<h4>WHY INTEL ONEAPI</h4>
Intel oneAPI is a software development toolkit that provides a unified programming model for developing high-performance applications across a range of architectures, including CPUs, GPUs, FPGAs, and AI accelerators. It is designed to help developers optimize their code for the specific hardware they are targeting, making it easier to achieve maximum performance.

![](https://user-images.githubusercontent.com/90272634/230717338-f2dc33e7-31df-4dc0-98f1-9074cb7252e2.png)

## Abstract
This Project is based upon collection of images from phone application's and usinng Deep Learning
Technique( Mask RCNN ), we have trained a custom machine learning model for detection of potholes
inside images and plot them on google maps,which includes the size of the pothole inside image.

Pothole detection Accuracy **__81%__** in different environments


<h4>Pothole Detected</h4>

![](https://github.com/kavinvengidu/Pothole_Detection_IntelOneAPI/blob/main/ResNet50/val_batch2_pred%20(3).jpg)
![](https://github.com/kavinvengidu/Pothole_Detection_IntelOneAPI/blob/main/ResNet50/val_batch2_pred%20(4).jpg)



## Team

- [Kavin V](https://www.linkedin.com/in/kavin-v-8028b9229/)
- [Harish R](https://www.linkedin.com/in/harish-r-b6b045229/)


## SETUP
We have used variety of Datasets  :

Install **youtube-dl** to __download files from google drive__ directly in terminal
```
https://github.com/ytdl-org/youtube-dl#installation
```
#### Training Dataset
To increase the model accuracy , For the training dataset we have trained them with
- Original Dataset Links
```
PotHole Detection DataSet
```
If you want to add your own dataset into our dataset. We have **resized all the images** for faster processing to **800x800**, Please do same with your images too
```python
from PIL import Image
import os
from resizeimage import resizeimage

count = 0

for f in os.listdir(os.getcwd()):
    try:
        with Image.open(f) as image:
            count +=1
            cover = resizeimage.resize_cover(image, [800,800])
            cover.save('pgm-1_{}.jpg'.format(count),image.format)
            print(count)
            os.remove(f)
    except(OSError) as e:
        print('Bad Image {}{}'.format(f,count))
```


We have also done annotion of all the images present there,
Annotion images

- For Annotation of images we have used roboflow
````
https://roboflow.com/
````
**__After annotion around 1000 images then we create this dataset__**


**Download these files**

| Folder Name        | Download Link           |
| -------------------|:-----------------------:|
| Roboflow | [link](https://public.roboflow.com/object-detection/pothole/1) |
| Roboflow      | [link](https://universe.roboflow.com/hackthethong/pothole-detection-gmnid)     |

We have created this Dataset for final testing of the model
This folder contains videos and photos that we recorded in May 2019
**[Test Dataset Download Link](https://drive.google.com/drive/u/2/folders/1duZ9O0If8mpHk8lZkFHQifv5R8z4dcKx)**


**For custom Training Process**

extract the zip files and create a folder named as "customImages" and move both folders
(train) & (val) folder directly inside it and then run the command

Structure for the whole Test Dataset Links
````
├── test_dataset
├──----- Photos
├──----- IMG_7300.MOV
├──----- IMG_7301.MOV
├──----- IMG_7310.MOV
├──----- IMG_7311.MOV
├──----- IMG_7312.MOV
````
<h3>Confusion Matrix</h3>

![](https://github.com/kavinvengidu/Pothole_Detection_IntelOneAPI/blob/main/Images/confusion_matrix%20(1).png)

<h3><b>Correlogram</b></h3>

![](https://github.com/kavinvengidu/Pothole_Detection_IntelOneAPI/blob/main/Images/labels_correlogram.jpg)





