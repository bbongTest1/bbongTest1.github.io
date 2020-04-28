---   
description: 本文介绍DBR中针对DPM这一特定场景的相关参数及使用
title: 如何解码DPM
keywords: DPM, Direct Part Mark
---
# 如何解码DPM
DPM（Direct Part Mark）是一种特殊的标识制作技术，该技术直接在零部件（金属、塑料等）表面上做标识，不同于一般场景下的条码，DPM 经常会存在零部件表面的反光、低对比度、背景等问题， DBR 默认情况下可能无法很好地处理这些问题，因此我们通过配置 `DPMCodeReadingModes` 来针对性的处理这些问题。以下是DPM的两个示意图。

![DPM sample image1][1]
![DPM sample image2][2]

## 参数的配置使用
要使用 DBR 针对 DPM 的功能，需要同时配置定位模式 `LM_STATISTICS_MARKS` 和 `DPMCodeReadingModes`。 `LM_STATISTICS_MARKS` 是专门针对类似 DPM 这种情况的基于点阵的定位方式，它保证了 DBR 可以顺利定位 DPM 码区。 `DPMCodeReadingModes` 则是配置了对于 DPM 码区采样解码的模式。

为了方便实际使用过程中参数的配置，当你设置 `DPMCodeReadingModes` 为 `DPMCRM_GENERAL` 后, DBR 将会自动开启定位模式 `LM_STATISTICS_MARKS`，因而不需要再单独设置。

## 示例
下面我们通过 RuntimeSetting 和 Json 模板两种方式演示参数的配置使用。
- 通过RuntimeSetting设置
```c++
CBarcodeReader* reader = new CBarcodeReader();  
reader->InitLicense("这里填入你的license");  
PublicRuntimeSettings* runtimeSettings = new PublicRuntimeSettings();  
reader->GetRuntimeSettings(runtimeSettings); //取出当前的模板参数  
runtimeSettings->furtherModes.dpmCodeReadingModes[0] = DPMCRM_GENERAL; //开启DPM
char sError[512];  
reader->UpdateRuntimeSettings(runtimeSettings, sError, 512); //更新模板参数
reader->DecodeFile("这里填入你的文件路径", ""); //解码
TextResultArray* paryResult = NULL;  
reader->GetAllTextResults(&paryResult); //拿出解码结果
CBarcodeReader::FreeTextResults(&paryResult);  
delete runtimeSettings;  
delete reader;  
```

- 通过Json模板设置
```Json
{    
    "Version":"3.0",    
    "ImageParameter":    
    {    
         "Name":"IP1",    
         "BarcodeFormatIds":["BF_ALL"],        
         "DPMCodeReadingModes":["DPMCRM_GENERAL"]
     }    
}   
```

[1]:assets\dpm-decoding\DPM-sample1.png
[2]:assets\dpm-decoding\DPM-sample2.png