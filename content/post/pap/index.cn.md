---
author: Rui Xiao
title: 细支气道腔显像分析
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

# 研究文章

[细支气道腔显像分析：肺结构的定量和表征，用于评估实质破坏. **Xiao R, Goldklang MP, D'Armiento JM.**](http://www.ncbi.nlm.nih.gov/pubmed/27373990)

[*美国呼吸细胞分子生物学杂志* 2016年11月;55(5):708-715.](http://www.atsjournals.org/toc/ajrcmb/55/5)

{{< gallery match="process/*" sortOrder="asc" rowHeight="60" margins="5" thumbnailResizeOptions="600x600 q90 Lanczos" showExif=true previewType="blur" embedPreview=true loadJQuery=true >}}


# 软件下载和截图

[Windows 下载链接](https://github.com/ruixiao85/ParenchymalAirspaceProfiling/releases/tag/2020.02.08.33)

{{< gallery match="screenshot/*" sortOrder="asc" rowHeight="200" margins="5" thumbnailResizeOptions="600x600 q90 Lanczos" showExif=true previewType="blur" embedPreview=true loadJQuery=true >}}

# 更新日志

1. 在二值化设置->全局阈值下，相对阈值设置改为从直方图中查找特定百分位数，这比基于平均亮度值增加/减少一个整数更准确。
1. 在常规设置下，添加了“裁剪比例”，因为为大型图像找到正确的阈值可能很耗时。 此裁剪比例将在调整大小后应用，并仅保留图像的中心部分 (0.5 => 裁剪到原始大小的一半)。 如果您只需要分析图像的中心部分或节省调整大型图像设置的时间，这尤其有用。
1. 除了现有常规设置下的“白平衡”之外，还添加了“黑色电平”，以使用户能够更多地控制图像亮度和对比度。 通常情况下，收集的图像对比度相对较低，这会使阈值处理变得困难。 此外，在 Photoshop 中为每个图像调整对比度可能是一个乏味的过程。 现在您可以结合使用“黑色电平”和“白平衡”来增强对比度并继续对图像进行二值化。
1. 错误修复。 最近我添加了一个到“缩放比例”的复选框，允许用户轻松打开/关闭此功能。 当关闭时，无论用户输入什么，缩放比例都应始终为 1。 但是，在以前的版本中，开关确实会影响图像大小调整，但后续计算仍然采用缩放比例输入。 此错误已在此版本中修复。 现在，如果开关关闭，则缩放比例输入将被忽略并设置为 1 进行计算。
1. 组织部分 (TF) 和 导管/破坏性与肺泡比率 (D2A = DF/AF) 已添加到数据报告中。 TF szczególnie pomocny do wykrywania tkanki bliznowatego i zmian grubości ściany pęcherzyków płucnych (since various reasons, including those mentioned above and thickness of each section, can affect tissue fraction, D2A (Ductal/Destructive to Alveolar Ratio, DF/AF) was introduced to make comparisons only between different categories of airspaces, other than the tissue)。 D2A 参数经过测试，与 DF 相比，对检测轻度肺气肿更敏感和鲁棒。
1. 输入参数之一的更改。 像素比例，以前是 µm/px -> 现在是 px/um。 更直观地讲，更高的放大倍率会使该参数的值更高。

# 软件文档 

[PAP_Readme_2016.5.30.pdf](PAP_Readme_2016.5.30.pdf)

# 教程视频

{{< youtube 4DIkx2ZCJ3w >}}

{{< youtube occ3jY-dgKo >}}

