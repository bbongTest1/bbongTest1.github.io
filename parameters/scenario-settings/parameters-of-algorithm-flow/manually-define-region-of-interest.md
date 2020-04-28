---   
description: 本文介绍DBR的ROI(Region Of Interest)、适用场景、手动定义方式和可配置参数
title: 如何手动定义DBR的ROI及其配置
keywords: ROI Region-Of-Interest RegionDefinition
---
# 如何手动定义DBR的ROI及其配置
DBR默认情况下在整张图片的范围内进行码区的定位和解码，但是如果用户关心的是某些特定区域而非整个图片范围，则可以通过 RegionDefinition 的相关参数定义 Region Of Interest，简称 ROI。定义特定区域后，DBR仅在定义区域内定位码区和解码，有利于提高运行的速度。本文会介绍 ROI 的定义方式和可配置参数 `ExpectedBarcodesCount`、`BarcodeFormatIds`，`BarcodeFormatIds_2`、`FormatSpecificationNameArray`。
## ROI 的定义 RegionDefinition
如果用户关心的只是图像某些特定区域，那么在Json中，通过 `RegionDefinition` 对象进行定义，可以定义一个或多个，需要指定 ROI 的四角坐标 `Top`，`Left`，`Right`，`Bottom` 和不同的 `Name`。参数 `MeasuredByPercentage` 用来指定 ROI 的四角坐标单位是像素还是百分制，百分制单位以原图宽高为100%标准。

要使用定义的 `RegionDefinition`，通过 `RegionDefinitionNameArray` 指定要使用的 Name。
## ROI 的 ExpectedBarcodesCount
`RegionDefinition` 内可以通过 `ExpectedBarcodesCount` 来指定该区域内的期待解码数量。明确的期待解码数量有利于帮助 DBR 判断是否已经满足要求并及时退出。
## ROI 的待处理码型 BarcodeFormatIds，BarcodeFormatIds_2
这两个参数设置该 ROI 内要处理的码型。明确的配置码型有利用提高 DBR 的处理速度，否则 DBR 有可能在无关的码型上浪费时间。
## ROI 使用的特定码型配置 FormatSpecificationNameArray
此参数设置当前 ROI 所使用的 `FormatSpecifications` 对应的 Names。设置后，该region将使用对应的 FormatSpecifications 配置。默认值为空，使用全局的 FormatSpecifications 配置。如果你想对 ROI 内的某些特定码型进行配置，应该使用这个参数。关于 `FormatSpecifications` 的详细说明参考我们的文档 [特定码型的配置参数]([1])。
## 示例
下面分别使用 RuntimeSetting 和 Json 模板两种形式来演示 `RegionDefinition` 的参数用法。
- RuntimeSetting
```c++
CBarcodeReader* reader = new CBarcodeReader();     
reader->InitLicense("这里填入license");    
PublicRuntimeSettings* runtimeSettings = new PublicRuntimeSettings();     
reader->GetRuntimeSettings(runtimeSettings); //取出当前的模板参数    
runtimeSettings->region.regionTop = 10;         
runtimeSettings->region.regionBottom = 50;      
runtimeSettings->region.regionLeft = 20;        
runtimeSettings->region.regionRight = 30;      
runtimeSettings->regionMeasurdByPercentage = 1; // 以百分比为单位定义 Region 范围  
char sError[512];     
reader->UpdateRuntimeSettings(runtimeSettings, sError, 512); //更新模板参数    
reader->DecodeFile("这里填入文件路径", ""); //解码    
TextResultArray* paryResult = NULL;     
reader->GetAllTextResults(&paryResult); //拿出解码结果    
CBarcodeReader::FreeTextResults(&paryResult);     
delete runtimeSettings;     
delete reader;  
```
- Json 模板
```json
{ 
    "ImageParameter": {
        "BarcodeFormatIds": ["BF_ALL"],
        "RegionDefinitionNameArray": ["RP_1", "RP_2"]
    }, 
    "RegionDefinitionArray": [
        {
            "Name": "RP_1",   
            "BarcodeFormatIds": ["BF_CODE_39"],
            "Top": 20,         
            "Bottom": 80,      
            "Left": 20,        
            "Right": 80,      
            "ExpectedBarcodesCount": 10,
            "MeasuredByPercentage": 0
        }, 
        {
            "Name": "RP_2", 
            "BarcodeFormatIds": ["BF_CODE_93"], 
            "BarcodeFormatIds_2": ["BF_DOTCODE"], 
            "Top": 30, 
            "Bottom": 70, 
            "Left": 30, 
            "Right": 80, 
            "MeasuredByPercentage": 1
        }
    ], 
    "Version": "3.0"
}
```

[1]: 特定码型的配置参数.md