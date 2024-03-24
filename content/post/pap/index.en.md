---
author: Rui Xiao
title: Parenchymal Airspace Profiling
date: 2016-11-30
thumbnail:
    src: '/images/post_pap_journal_microscope.jpg'
    alt: 'post pap journal microscope'
    object_position: '0% 0%'
    height: 200px
showToc: true
categories: ["work"]
tags: ["text", "picture", "video"]
badges:
    github:
        subject: GitHub
        status: Check it on GitHub
        icon: github
        url: https://github.com/ruixiao85/ParenchymalAirspaceProfiling
        color: grey
        label: ""
    kofi:
        subject: kofi
        status: Buy me a coffee ❤️
        icon: kofi
        label: ""
        url: https://ko-fi.com/ruixiao85
---

# Research Article

[Parenchymal Airspace Profiling: Sensitive Quantification and Characterization of Lung Structure Evaluating Parenchymal Destruction. **Xiao R, Goldklang MP, D'Armiento JM.**](http://www.ncbi.nlm.nih.gov/pubmed/27373990)

[*Am J Respir Cell Mol Biol.* 2016 Nov;55(5):708-715.](http://www.atsjournals.org/toc/ajrcmb/55/5)

{{< gallery match="process/*" sortOrder="asc" rowHeight="60" margins="5" thumbnailResizeOptions="600x600 q90 Lanczos" showExif=true previewType="blur" embedPreview=true loadJQuery=true >}}


# Software Download & Screenshots

[Download link for Windows](https://github.com/ruixiao85/ParenchymalAirspaceProfiling/releases/tag/2020.02.08.33)

{{< gallery match="screenshot/*" sortOrder="asc" rowHeight="200" margins="5" thumbnailResizeOptions="600x600 q90 Lanczos" showExif=true previewType="blur" embedPreview=true loadJQuery=true >}}

# Update Logs

1. Under Binarization Settings->Global Thresholding, relative threshold settings were changed to find a specific percentile from the histogram, which is more accurate than +/- an integer based on mean brightness value.
1. Under General Settings, "crop ratio" was added because finding the correct threshold for large images can be time-consuming. This crop ratio will be applied after resizing and only keep the center portion of your image (0.5 => crop to half of the original size). It's particularly helpful if you only need to analyze the center of your images or save time on tweeking the settings for large images.
1. In addition to existing "White Balance" under General Settings, "Black Level" was added to give user more control over image brightness and contrast. Often times, the images collected have relatively low contrast, which will make the thresholding difficult. Besides, adjusting contrast in Photoshop for each image can be a tedious process. Now you can use "Black Level" and "White Balance" together to enhance the contrast and continue to binarize your image.
1. Bug fix. Recently I added a check box to "Resize Ratio" to allow users to easily toggle on/off this feature. When turned off, the resize ratio should always be 1 regardless of the user input. However, in the previous version the switch did affect image resizing but the subsequent calculation still took the resize ratio input. This bug was fixed in this version. Now if the switch is off, resize ratio input will be ignored and set as 1 for calculation.
1. Tissue Fraction (TF) and Ductal/Destructive to Alveolar Ratio (D2A = DF/AF) have been added to the data report. TF is particularly helpful to detect scarring tissue and changes in alveolar wall thickness. Since various reasons, including those mentioned above and thickness of each section, can affect tissue fraction, D2A (Ductal/Destructive to Alveolar Ratio, DF/AF) was introduced to make comparisons only between different categories of airspaces, other than the tissue. The D2A parameter has been tested and found to be more sensitive and robust in detecting mild emphysema, compared to DF.
1. Changes to one of the input parameters. Pixel Scale, previously µm/px -> now px/um. More intuitively, higher magnification will get higher value for this parameter.

# Software Documentation

[PAP_Readme_2016.5.30.pdf](PAP_Readme_2016.5.30.pdf)

# Tutorial Video

{{< youtube 4DIkx2ZCJ3w >}}

{{< youtube occ3jY-dgKo >}}


