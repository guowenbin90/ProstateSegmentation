# Prostate segmentation in Micro-Ultrasound images using deep neural networks

### Table of Contents

1. [Introduction](#Introduction)
2. [Objective](#Objective)
3. [Method](#Method)
4. [Acknowledgements](#Acknowledgements)
5. [Cite this paper](#Citation)

## Introduction<a name="Introduction"></a>
### Prostate Cancer: 
- The most common solid malignancy among American men.
- 2022 estimated new cases: 268,490

### Cancer identification tools: 
1. Conventional Ultrasound
2. Magnetic Resonance Imaging (MRI)
3. Micro-Ultrasound

### Micro-Ultrasound:
1. High resolution (29MHz)
2. Sensitive to significant prostate cancer
3. Real-time scan during in-bore biopsy

### Problems:
1. Manual prostate segmentation:
2. Time-consuming
3. Subject to surgeons’ experience level
4. A wide range of shapes and sizes
5. Ambiguity of prostate boundaries

## Objective<a name="Objective"></a>
Perform automated prostate capsule segmentation using the U-Net deep neural network framework

<img src="https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/ProstateSegmentation_Frame21.png" width=80% height=80%>

## Method<a name="Method"></a>
### Dataset preprocessing 
Check code file [DataPreprocessing.ipynb](https://github.com/guowenbin90/ProstateSegmentation/blob/main/DataPreprocessing.ipynb) 
1. Generate masks and images from DICOM modality images based on the primary key **SOP Instance UID**.
2. Images were exported from the metadata in the Dicom files. Or we could export images from the Weasis software.  
3. Masks were graphic annotations which were consist of an array of x, y coordinates. OpenCV was used to draw the Convex polyline and set up the black and white colors.
4. Rename files using UID. The (0008, 0018) SOP Instance UID in the metadata likes this. <img src="https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/SOP%20Instance%20UID.JPG">
5. Save png files to the folders <img src="https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/Exported%20images%20and%20masks.JPG">
6. Two dictionaries based on the SOP Instance UID. One is the image dictionary (X), and another is the mask dictionary (Y). These are the preprocessing of the images and annotations for the model training. X is the feature, and Y is the target value in the training and prediction.
### Dataset training using modified U-Net architecture
Check code file [PCa-UNet-dataset-training.ipynb](https://github.com/guowenbin90/ProstateSegmentation/blob/main/PCa-UNet-dataset-training.ipynb)
IoU in the three different sets            |  10-fold cross-validation
:-----------------------------------------:|:-------------------------:
![](https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/IoU.png)  |  ![](https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/CrossValidation.png)

## Acknowledgement<a name="Acknowledgements"></a>
Prostate Cancer Foundation

## Cite this paper<a name="Citation"></a>
[Full PDF file](https://research.dwi.ufl.edu/page/prostate-capsule-segmentation-in-micro-ultrasound-images-using-deep-neural-networks/)

Guo, Wenbin, Wayne Brisbane, Rani Ashouri, Brianna Nguyen, and Angelos Barmpoutis. "Prostate Capsule Segmentation in Micro-Ultrasound Images Using Deep Neural Networks." 
In 2023 IEEE 20th International Symposium on Biomedical Imaging (ISBI), pp. 1-5. IEEE, 2023. DOI: [10.1109/ISBI53787.2023.10230652](https://doi.org/10.1109/ISBI53787.2023.10230652)
