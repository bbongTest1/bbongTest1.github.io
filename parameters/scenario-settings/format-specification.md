---   
description: 本文介绍使用DBR时如何配置参数FormatSpecification来对某一特定码型进行配置
title: 特定码型的配置参数 
keywords: nonstandard barcode, specification
---
# 特定码型的配置参数
如果你想针对某些特定码型进行参数配置，可以使用 `FormatSpecification`，如果 `FormatSpecification` 配置与全局的 `ImageParameter` 冲突，那么`FormatSpecification` 的配置有更高的优先级。本文介绍相关的参数及其适用场景。

-  [BarcodeFormatIds,BarcodeFormatIds_2](#BarcodeFormatIds,BarcodeFormatIds_2)

    指定当前FormatSpecification配置应用于的码型

-  [MirrorMode](#MirrorMode)

    指定解码时的镜像处理模式
 
-  [RequireStartStopChars](#RequireStartStopChars)

    指定解码时是否需要开始符与结束符

-  [AllModuleDeviation](#AllModuleDeviation)

    指定条码的码条尺寸与标准条码码条尺寸的偏差值

-  [HeadModuleRatio，TailModuleRatio](#HeadModuleRatio，TailModuleRatio)

    指定非标准1D条码头部,尾部的自定义码条数量和尺寸比例

-  [StandardFormat](#StandardFormat)

    指定非标准1D的字符集参考的标准条码码型

-  [AustralianPostEncodingTable](#AustralianPostEncodingTable)

    指定 AustralianPost Code 中 Customer information Field 使用的解码表

-  [MinQuietZoneWidth](#MinQuietZoneWidth)

    指定条码静区的最小宽度

-  [ModuleSizeRangeArray](#ModuleSizeRangeArray)

    指定搜寻条码的码条尺寸范围

- [其他](#其他)

## BarcodeFormatIds,BarcodeFormatIds_2
此参数指定当前FormatSpecification配置应用于的码型。
## MirrorMode
此参数指定解码时的镜像处理模式。因为镜头拍摄等原因，有时候会出现图像与真实场景刚好是镜像的情况，对于2D码来说，镜像可能会导致DBR无法正常解码，可配置该参数处理这种情况。DBR 默认用 [MM_NORMAL]() 来进行处理，即只会尝试解原图。   
该参数有以下枚举


| 枚举名    | 枚举值 | 备注                 |
|-----------|--------|----------------------|
| MM_NORMAL | 0x01   | 保持图像原样进行解码处理        |
| MM_MIRROR | 0x02   | 对图像镜像处理后进行解码处理         |
| MM_BOTH   | 0x04   | 以上两种方式都尝试进行。默认值 |

下面是正常QR和镜像QR的两个示例图：

![normal QR][1]&emsp;&emsp;&emsp; ![mirror QR][2]

&emsp;&emsp; 正常QR&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 镜像QR

下面是示例Json模板，在该示例中我们配置QR码型进行镜像处理。
```javascript
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is mirror mode demonstrate", 
        "FormatSpecificationNameArray": ["FP_1"]
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds": ["BF_QR_CODE"], 
            "MirrorMode":"MM_MIRROR"
        }
    ], 
    "Version": "3.0"
}   
```

## RequireStartStopChars
1D条码通常有固定的开始符和结尾符，DBR找到头尾符才能正常解码，但是因为某些原因，实际情况下可能出现缺失头尾符的情况，此参数是为了读取这种非标准条码而设计，用于指定1D解码时是否需要找到开始符与结束符。该参数可以设置为0或者1。0代表不需要开始符与结束符；1则代表需要开始符与结束符。

下图是一个标准的Code39，有正常的开始符和结束符

![standard-code39][3]

下图是一个同样码值但是没有开始符和结束符的Code39

![code39 without start and end pattern][4]

下面是示例Json模板，在这个例子中我们设置了解码Code39不需要开始符和结尾符。

```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is RequireStartStopChars demonstrate", 
        "FormatSpecificationNameArray": ["FP_1"]
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds": ["BF_CODE_39"],                      
            "RequireStartStopChars":0
        }
    ], 
    "Version": "3.0"
}   
```

## AllModuleDeviation

该参数指定非标准1D码型的宽度偏差值，单位为moduleSize，默认值为0。

因为某些原因，实际的1D条形码宽度相对于标准条码宽度有可能出现偏大一定moduleSize或偏小一定的modulesize。DBR默认情况可能无法处理这些非标准情况，可以通过设置该参数的偏差值来处理这些问题。

该参数使用时需要以下参数配合使用   
- `FormatSpecification.BarcodeFormatIds_2`  
`FormatSpecification.BarcodeFormatIds_2` 需要设为 `NON_STANDARD_BARCODE`，代表我们现在要定义一种新的非标准码型
- `FormatSpecification.StandardFormat`    
`StandardFormat` 要设置成某一特定1D码型，代表我们当前定义的非标准码型的字符标准是参考哪一具体码型，比如设为 `BF_CODE128`
- `ImageParameter.BarcodeFormatIds_2`   
`ImageParameter.BarcodeFormatIds_2` 需要设为 `NON_STANDARD_BARCODE`，代表我们需要处理刚刚定义的非标准码型

下面我们使用一个实际的例子来说明，下图是一个标准的Code128，moduleSize为2px

![standard-code128][5]

接下来是一个非标准的Code128，该条码的每一段码条都比标准码条多了4px，即 2 module size

![code128-deviation][6]

正常解码无法解出码值，这样的情况我们可以设置AllModuleDeviation为2，这样在解码时就会考虑2倍moduleSize的偏差值，从而正确解出码值。下面的Json模板演示完整的配置。

```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is deviation demonstrate", 
        "FormatSpecificationNameArray": ["FP_1"],
        "BarcodeFormatIds_2": ["BF2_NONSTANDARD_BARCODE"]
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds_2": ["BF2_NONSTANDARD_BARCODE"],                          
            "StandardFormat": "BF_CODE_128",    
            "AllModuleDeviation":2          
           
        }
    ], 
    "Version": "3.0"
}   
```

## HeadModuleRatio，TailModuleRatio
通常1D条码的开始符和结束符有着固定的比例关系，但在实际场景下也会出现开始符和结尾符是非标准比例关系的情况，DBR正常无法解出这种条码。如果条码的比例关系是统一的偏差，那么考虑 [`AllModuleDeviation`](##AllModuleDeviation) 参数，如果是无规则的偏差，那么可以利用 `HeadModuleRatio` 、 `TailModuleRatio` 自定义头尾的比例关系。

在自定义头尾比例关系时还需要以下参数配合使用   
- `FormatSpecification.BarcodeFormatIds_2`  
`FormatSpecification.BarcodeFormatIds_2` 需要设为 `NON_STANDARD_BARCODE`，代表我们要定义一种非标准码型
- `FormatSpecification.StandardFormat`    
`StandardFormat` 要设置成某一特定1D码型，代表我们当前定义的非标准码型的字符集标准是参考哪一具体码型。如果设为 `BF_CODE128`，那么还需要额外用 `Code128Subset` 指定字符集具体是A、B、C中的哪一个。
- `ImageParameter.BarcodeFormatIds_2`   
`ImageParameter.BarcodeFormatIds_2` 需要设为 `NON_STANDARD_BARCODE`，代表我们需要处理刚刚定义的非标准码型

下面我们使用一个非标准的Code128来演示说明。如下图，它的开始符比例关系为2：1：1：3：3：1，不符合code128标准定义的开始符的比例关系，结束符的比例关系为2：3：3：2：2：2：3也不符合标准的结束符。

![nonstandard-start-end][7]

同样码值的标准条码如下所示

![standard-start-end][8]

DBR默认是无法正确读取条码的。这种情况下我们将 `HeadModuleRatio` 和 `TailModuleRatio` 分别设为 `"211331"` 和 `"2332223"`， `Code128Subset` 设为 `"C"` 则能够解出该非标准条码。完整的Json配置如下

```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is HeadModuleRatio and TailModuleRatio demonstrate", 
        "FormatSpecificationNameArray": ["FP_1"],
        "BarcodeFormatIds_2": ["BF2_NONSTANDARD_BARCODE"],  
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds_2": [                 
                "BF2_NONSTANDARD_BARCODE"
            ],  
            "StandardFormat":"BF_CODE_128", 
            "HeadModuleRatio": "211331",          
            "TailModuleRatio": "2332223", 
            "Code128Subset": "C"                 
        }
    ], 
    "Version": "3.0"
}   
```

## StandardFormat

此参数指定非标准1D的字符集参考的标准条码码型。要与 [`AllModuleDeviation`](##AllModuleDeviation)、[`HeadModuleRatio`](##HeadModuleRatio，TailModuleRatio)、[`TailModuleRatio`](##HeadModuleRatio，TailModuleRatio) 配合使用，这里不再详细介绍。

## AustralianPostEncodingTable

AustralianPost Code存在一段客户信息区，可以使用标准中定义的两张解码表（N table，C table）来解码，通过设置该参数来选择 N table 或 C table 来进行解码，有关这两张解码表的具体定义请参考AustralianPostcode[标准文档](https://auspost.com.au/content/dam/auspost_corp/mediai/documents/customer-barcode-technical-specifications-aug2012.pdf)中的说明。

该参数可设置为”C”或者”N”，默认值为”C”。若设置为”C”则使用C table解码，”N”使用N table解码。

该参数使用时，`FormatSpecification.BarcodeFormatIds_2` 需要同时设为 `BF2_AUSTRALIANPOST`


## MinQuietZoneWidth

标准条码的两侧应该有足够的留白作为静区。但是实际的图像中，有可能没有足够的留白空间，DBR对于这种情况可能无法正常解码，通过 `MinQuietZoneWidth` 来设置最小静区的大小，单位为ModuleSize，默认值为4。

![barcode-quietzone-definition][9]

下图是一个静区很窄的例图：

![barcode-narrow-wide-quietzone][11]

如果我们设置了如下模板，静区要求 3 moduleSize，这样的话 DBR 没法解出这张图，`MinQuietZoneWidth` 需要更改为1或者更小，即可正常解码。

```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is quiet zone demonstrate", 
        "FormatSpecificationNameArray":["FP_1"],
        "DeblurLevel": 1
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds": ["BF_CODE_128"],                
            "MinQuietZoneWidth":3
        }
    ], 
    "Version": "3.0"
}   
```

## ModuleSizeRangeArray

此参数用于指定在搜寻条码时，条码的ModuleSize需要满足的范围，不满足条件的条码将不会被解出。

默认值为空，意为不对条码的moduleSize做限制。

设置范围为[0,0x7fffffff],单位为像素。

示例Json模板：

```json
{
    "ImageParameter": {
        "Name": "ImageParameter1", 
        "Description": "This is template demonstrate", 
        "FormatSpecificationNameArray":["FP_1"]
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FP_1", 
            "BarcodeFormatIds": [                 
                "BF_CODE_39"
            ], 
            "ModuleSizeRangeArray"：[
                {
                  "MaxValue":100,
                  "MinValue":10
                }
            ] 
        }
    ], 
    "Version": "3.0"
}   
```



## 其他
`FormatSpecification` 中的其他参数的用法我们会在在其它相关文档中详细介绍，本文不再展开说明
- BarcodeAngleRangeArray、BarcodeBytesLengthRangeArray、BarcodeHeightRangeArray、BarcodeTextLengthRangeArray、BarcodeWidthRangeArray、BarcodeTextRegExPattern    
参考文档 [解码结果]([12])

- DeblurLevel   
参考文档 [通常的采样解码]([13])

- AccompanyingTextRecognitionModes    
参考文档 [RecogniseAcompanyingText]([14])


[1]:./assets/format-specification/normal-qr.png

[2]:./assets/format-specification/mirror-qr.png

[3]:./assets/format-specification/standard-code39.png

[4]:./assets/format-specification/code39-without-start-end.png

[5]:./assets/format-specification/standard-code128.png

[6]:./assets/format-specification/code128-deviation.png

[7]:./assets/format-specification/nonstandard-start-end.png

[8]:./assets/format-specification/standard-start-end.png

[9]:./assets/format-specification/barcode-quietzone-definition.png

[10]:./assets/format-specification/barcode-with-wide-quietzone.png

[11]:./assets/format-specification/barcode-with-narrow-quietzone.png

[12]:./parameters-of-algorithm-flow/recognise-acompanying-text.md

[13]:./parameters-of-algorithm-flow/recognise-acompanying-text.md

[14]:./parameters-of-algorithm-flow/recognise-acompanying-text.md































































































































































































































































































































































































































































































































-


