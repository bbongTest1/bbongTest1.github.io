---
title: 如何设置DBR的要处理码型和期待解码数量
description: 本文介绍如何设置DBR的待处理码型和期待的解码数量，及这些设置的作用。
keywords: barcode format, expected barcode counts
---

# 如何设置DBR的要处理码型和期待解码数量

DBR 可以处理市面上各种常见的码型，并且可以很好的支持图像中出现的多码场景。当然DBR在处理图像过程中，为了能兼顾所有支持的码型及解出图中出现的所有码，会付出一定的时间代价。如果你不希望这种消耗，那么通过 `BarcodeFormatIds`、`BarcodeFormatIds_2` 设置你关心的码型，通过 `ExpectedBarcodesCount` 设置你想要的的解码数量。

## `BarcodeFormatIds`、`BarcodeFormatIds_2`

这两个参数用于设置用户要的解码码型。未设置的码型 DBR 不会去处理，通过排除你不关心的码型可以加快 DBR 的处理速度。参数的具体枚举值参考我们的 API 文档 [`BarcodeFormatIds`][1]、 [`BarcodeFormatIds_2`][2]

## `ExpectedBarcodesCount`

这个参数用来设置图像期望的解码数量。当解出的码数量大于等于该参数时，DBR算法会终止。DBR 可以很好的处理图像中同时存在多个码的情况，根据实际需求，合理设置期望的码数量，可以使得DBR算法及时终止，提高速度。

## 示例

下面演示 RuntimeSetting 和 Json 模板两种配置方式

```c++
CBarcodeReader* reader = new CBarcodeReader();   
reader->InitLicense("这里填入你的license");  
PublicRuntimeSettings* runtimeSettings = new PublicRuntimeSettings();   
reader->GetRuntimeSettings(runtimeSettings); //取出当前的模板参数  
runtimeSettings->barcodeFormatIds = BF_ALL; //设置码型，这里设置BF_ALL，也就是所有barcodeFormatIds里的码型  
runtimeSettings->barcodeFormatIds_2 = BF2_NULL; //设置码型2，这里设置BF2_NULL，也就是不添加barcodeFormatIds_2里的码型  
runtimeSettings->expectedBarcodesCount = 1; //设置期望的解码数量为1  
char sError[512];   
reader->UpdateRuntimeSettings(runtimeSettings, sError, 512); //更新模板参数  
reader->DecodeFile("这里填入你的文件路径", ""); //解码  
TextResultArray* paryResult = NULL;   
reader->GetAllTextResults(&paryResult); //拿出解码结果  
CBarcodeReader::FreeTextResults(&paryResult);   
delete runtimeSettings;   
delete reader;  
```

```json
{    
    "Version":"3.0",    
    "ImageParameter":    
    {    
        "Name":"IP1",    
        "BarcodeFormatIds":["BF_ALL"],
        "BarcodeFormatIds_2":["BF2_NULL"],        
        "ExpectedBarcodesCount":1
    }    
}   
```



[1]: test.html
[2]: test2.html