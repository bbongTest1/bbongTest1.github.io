---   
description:本文介绍DBR算法中的纹理检测的相关参数及其适用场景、调整方法
title: 如何处理图像纹理
keywords: texture detection
---

# 如何处理图像纹理
纹理场景的图像，例如花纹背景、屏幕条纹等，有可能对DBR产生耗时增加、误定位等不良影响，DBR 提供 `TextureDetectionModes` 来应对纹理情况。可配置一个或多个 `TextureDetectionMode`, DBR会依次循环配置的mode来进行处理。
`TextureDetectionMode` 的枚举如下：
 
枚举名|枚举值|备注|
---|:--:|---:|
TDM_SKIP|0x00000000|跳过纹理检测|
TDM_GENERAL_WIDTH_CONCENTRATION|0x00000002|通用的纹理检测，默认值|
TDM_AUTO|0x00000001|等同于 `TDM_SKIP`|

`TDM_GENERAL_WIDTH_CONCENTRATION` 还有一个 `Sensitivity` 可以设置, 用来控制纹理检测的敏感度，该值越大纹理检测效果越明显，该值的默认值为5，取值范围为[1,9]。

## 何时需要纹理检测、如何调整相关参数
纹理检测适用于有纹理背景的图像，可以通过中间结果 `IRT_BINARIZED_IMAGE` 观察二值图效果，来决定是否需要纹理检测，接下来我们用一个实际的屏幕纹理图片来演示何时需要纹理检测、如何调整相关的参数。

![texture-image-sample][1]

当我们不使用纹理检测功能，即设置 `TDM_SKIP` 时，利用中间结果 `IRT_BINARIZED_IMAGE` 我们可以观察到二值图是下图这样。该图的纹理非常严重，完全包围了码区。

![binary-before-texture-detect][2]

如果设置为 `TDM_GENERAL_WIDTH_CONCENTRATION` 时，我们可以观察到二值图如下。纹理有很好的被处理掉。这样的二值图对我们来说是非常理想的。

![binary-after-texture-detect][3]

如果你配置 `TDM_GENERAL_WIDTH_CONCENTRATION` 之后纹理没有被很好的处理，可以选择增大 `Sensitivity` 来尝试。
## 示例模板
```json
{
    "ImageParameter": {
        "BarcodeFormatIds": ["BF_ALL"],
        "TextureDetectionModes":[
            {
                "Mode":"TDM_GENERAL_WIDTH_CONCENTRATION", 
                "Sensitivity":5
            }
        ]
    },
    "Version": "3.0"
}
```
[1]:assets/texture-detection/texture-image-sample.png
[2]:assets/texture-detection/binary-before-texture-detect.png
[3]:assets/texture-detection/binary-after-texture-detect.png