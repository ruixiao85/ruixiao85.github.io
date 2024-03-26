---
author: Rui Xiao
title: Lung Neural Network
date: 2019-05-01
thumbnail:
    src: '/images/post_lnn.jpg'
    alt: 'post lung neural network'
    object_position: '0% 0%'
    height: 200px
showToc: true
categories: ["work"]
tags: ["text", "picture"]
badges:
    github:
        subject: GitHub
        status: Check it on GitHub
        icon: github
        url: https://github.com/ruixiao85/LungNeuralNet
        color: grey
        label: ""
    kofi:
        subject: kofi
        status: Buy me a coffee ❤️
        icon: kofi
        label: ""
        url: https://ko-fi.com/ruixiao85
---

# LungNeuralNet

We demonstrated that the CNNs, including U-Net and Mask R-CNN, are instrumental to provide:

- efficient evaluation of **pathological lung lesions**.
- detailed characterization of the **normal lung histology**.
- precise detection and classification for **BALF cells**.

Overall, these advanced methods allow improved efficiency and quantification of lung cytology and histopathology.
 
## Applications of U-Net like architectures

The convolutional neural network architecture used in this project was inspired by [U-Net](http://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/) and [dual frame U-Net](https://arxiv.org/abs/1708.08333) with added transfer learning from pre-trained models in keras ([keras-applications](https://keras.io/applications/)).

![alt text](images/train_unet.jpg?raw=true "train_unet")

### Lung Pathology

After training on **14** image pairs, the neural network is able to reach **>90%** accuracy (dice coefficient) in identifying lung parenchymal region and **>60%** for severe inflammation in the lung in the validation set.
The prediction results on a separate image, including segmentation mask and area stats, was shown below.

Multi-label overlay (blue: parenchyma, red: severe inflammation)

![alt text](images/36_KO_FLU_1_both.jpg?raw=true "both parenchyma and severe inflammation in the lung")

|   | Parenchyma  |  SevereInflammation |
|---|---|---|
| 36_KO_FLU_1.jpg | 836148 | 203466 |

### Lung Histology

After training and validating (3:1) on **16 whole slide scans**, the neural network is able to identify a variety of areas in a normal mouse lung section (equivalent to 10X, cropped from whole slide scan).

Variations of U-Nets were built to perform
 - **single-class segmentation**
    - output: sigmoid
    - loss: dice & binary crossentropy
    - metrics: dice
 - **multi-class segmentation**
    - output: softmax
    - loss: multiclass crossentropy
    - metrics: accuracy

Among them, dual-frame slightly outperform U-Net with single-frame.
Although more time consuming, single-class segmentation combined with argmax achieved a better classification results than those done by one multi-class segmentation model,
especially for the underrepresented categories.

The best results are listed below:
 - **single-class segmentation** (dice)
    - background: 97%
    - conducting airway: 84%
    - connective tissue: 83%
    - large blood vessel: 78%
    - respiratory airway: 97%
    - small blood vessel: 63%
 - **multi-class segmentation** (accuracy)
    - all six categories: 96%
    
These methods are helpful for identifing and quantifing various structures or tissue types in the lung and extensible to developmental abnormality or diseased areas.

Non-Parenchymal Region Highlighted Image

![alt text](images/027327_greenmark.jpg?raw=true "greem-marked image")

Six-Color Segmentation Map

![alt text](images/027327_pred.jpg?raw=true "6 color segmentation image")

## Applications of Mask R-CNN

Mask RCNN was developed by [Kaiming He, 2017](https://arxiv.org/abs/1703.06870) to simultaneously perform instance segmentation, bounding-box object detection, and keypoint detection.

This project was based on the implementation of [matterport](https://github.com/matterport/Mask_RCNN) with additional functionalities:
 - support more convolutional backbone, including vgg and densenet.
 - support large images by performing slicing and merging images & detections.
 - simulate bronchoalveolar lavage from background & representative cell images for efficient training.
 - batch-evaluate models for the mean average precision (mAP).

![alt text](images/train_mrcnn.jpg?raw=true "scheme")

### Broncho-alveolar Lavage Fluid Cytology

After training and validating (3:1) on 21 background image with 26 lymphocytes, 95 monocytes, and 22 polymorphonuclear leukocytes, the neural network is able to detect and categorize these cell types in a mouse lung bronchoalveolar lavage fluid (20X objective).

![alt text](images/mrcnn_simulate.jpg?raw=true "train with simulated images")
  
Within one day of training, the accuracy represented by mean average precision has reached 75% for all categories.
The accuracy is highest for the monocyte category.

![alt text](images/20x_balf_cells.jpg "cell detection and categorization results")

Data credits: Jeanine D'Armiento, Monica Goldklang, Kyle Stearns; Columbia University Medical Center