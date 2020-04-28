---
description: 本文介绍DBR利用OCR进行码区伴随文本识别的功能及相关参数的使用
title: 如何识别伴随文本
keywords: acompanyingText,OCR
---
# 如何识别伴随文本
在某些情景下，码区附近会有一些伴随文本，可能是码值也可能是其他额外信息。你可能需要这些伴随文本的信息进行码值校验、码区解码失败时的辅助信息或者满足其他需求。DBR提供了利用OCR进行伴随文本识别的功能，通过 `AcompanyingTextRecognitionModes` 进行配置，该参数是 `AcompanyingTextRecognitionMode` 的数组，可配置多个，DBR会依次循环每一个 mode 来处理。

`AcompanyingTextRecognitionMode` 有如下枚举值

| 枚举名    | 枚举值 | 备注                       |
|:-----------:|:--------:|:--------------------:|
| ATRM_SKIP | 0x00   | 不识别伴随文本            |
| ATRM_GENERAL | 0x01   | 识别伴随文本  |

## 默认范围的伴随文本识别
配置 `ATRM_GENERAL` 后，DBR即可进行默认范围内伴随文本识别。DBR会以成功解码的码区为基准，在其四周的较近的范围内寻找并识别可能存在的伴随文本。这适用于通常的情况，下面是一个示例图，DBR可以识别出红框标识出的伴随文本

![standard-acompanying-text][1]

Json模板示例
```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is acompanying text demonstrate", 
        "AcompanyingTextRecognitionModes":["ATRM_GENERAL"]
    }, 
    "Version": "3.0"
}  
```
## 自定义范围的伴随文本识别
某些场景下，你关心的伴随文本信息可能不在码区的附近，这种情况下可以码区为基准，自定义识别范围。通过设置 `bottom`，`left`，`right`，`top` 4个值来进行确定，单位是百分制，以码区的宽和高作为横向和纵向的100%，以码区左上角为基准原点。

我们以下图为例来进行说明。在这个示例中，我们想要识别绿框标识的数字，但是它距离码区有一点远，所以我们选择自定义识别范围。设置 `RegionBottom = -190`，`RegionLeft = -12`，`RegionRight = 85`，`RegionTop = -255`，该设置的范围在下图中以红色框标出。

![a card image demo that has a customed acompanying text recognition range][3]

示例Json模板：
```javascript
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is a acompanying text demonstrate", 
        "AcompanyingTextRecognitionModes":[
            {
                "Mode" : "ATRM_GENERAL",
                "RegionBottom" : -190,
                "RegionLeft" : -12,
                "RegionRight" : 85,
                "RegionTop" : -255
            }
        ]
    }, 
    "Version": "3.0"
}  
```
## 获取伴随文本结果
伴随文本的结果是作为类型为 `RT_STANDARD_TEXT` 的 `ExtendedResult` 储存于解码结果中。下面的示例程序演示了如何获取到伴随文本的识别结果。
```c++
CBarcodeReader * reader = new CBarcodeReader;
reader->InitLicense("your license here");
char error[512];
int ret = reader->InitRuntimeSettingsWithFile("JsonTemplate.txt",CM_OVERWRITE,error,512);
ret = reader->DecodeFile("image file path");
TextResultArray* pResults = NULL;
reader->GetAllTextResults(&pResults);
for(int resultId = 0; resultId < pResults->resultsCount; ++resultId)
{
    TextResult* pBarcode = pResults->results[resultId];
    string accompany;
    //循环所有的 ExtendedResult
    for(int extendId = 0; extendId < pBarcode->resultsCount; ++extendId)
    {
        PExtendedResult pExtend = pBarcode->results[extendId];
        if(pExtend->resultType == RT_STANDARD_TEXT)
        {
            unsigned char * accompanyStr = pExtend->accompanyingTextBytes;
            int strLen = pExtend->accompanyingTextBytesLength;
            accompany = string(accompanyStr,accompanyStr + strLen);
            break;
        }    
    }
    if(!accompany.empty())
    {
        cout << "accompanyText: " << accompany << endl;
    }
}
CBarcodeReader::FreeTextResults(&pResults);
delete reader;
```

[1]:assets\recognise-acompanying-text/standard-acompanying-text.png
[3]:assets/recognise-acompanying-text/acompanying-text-card.png