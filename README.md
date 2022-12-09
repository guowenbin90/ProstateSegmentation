# Prostate segmentation in Micro-Ultrasound images using deep neural networks

## Introduction
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

### Objective:
Perform automated prostate capsule segmentation using the U-Net deep neural network framework

## Method
### Dataset preprocessing 
Check [DataPreprocessing.ipynb](https://github.com/guowenbin90/ProstateSegmentation/blob/main/DataPreprocessing.ipynb) file
1. Generate masks and images from DICOM modality images based on the primary key **SOP Instance UID**.
2. Images were exported from the metadata in the Dicom files. Or we could export images from the Weasis software.  
3. Masks were graphic annotations which were consist of an array of x, y coordinates. OpenCV was used to draw the Convex polyline and set up the black and white colors.
4. Rename files using UID. The (0008, 0018) SOP Instance UID in the metadata likes this. <img src="https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/SOP%20Instance%20UID.JPG">
5. Save png files to the folders <img src="https://github.com/guowenbin90/ProstateSegmentation/blob/main/images/Exported%20images%20and%20masks.JPG">
6. Two dictionaries based on the SOP Instance UID. One is the image dictionary (X), and another is the mask dictionary (Y). These are the preprocessing of the images and annotations for the model training. X is the feature, and Y is the target value in the training and prediction.

## Acknowledgement
