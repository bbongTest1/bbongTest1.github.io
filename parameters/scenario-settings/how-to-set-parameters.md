---   
description: 本文介绍DBR修改配置的两种方式RuntimeSetting和Json模板，及其他们的语法规则
title: 如何设置 DBR 的 Parameters
keywords: DBR RuntimeSetting Json Template ImageParameter FormatSpecification
---
# 如何设置 DBR 的 Parameters
DBR提供了灵活的参数配置来满足用户不同场景下的需求。用户可以通过 RuntimeSetting 和 Json 模板两种方式来修改配置。
- RuntimeSetting   
RuntimeSetting是DBR运行时中的管理各种参数的对象。如果你需要程序运行时动态的改变DBR的配置，采用修改RuntimeSetting这一方式会是一个好的选择。
- Json 模板   
DBR提供的 Json 模板允许你以配置文件的形式来管理各种参数。如果你的应用场景相对固定，不需要频繁的更换DBR配置，Json 模板会是一个合适的选择。

接下来，我们会详细介绍两种方式。

## DBR的 RuntimeSetting 对象
`RuntimeSetting` 对象管理DBR运行时中的各种参数。用户可以在代码中通过修改 `RuntimeSetting` 中的字段值，来更改DBR配置，这一配置方式适用于有动态改变配置需求的场景。

首先需要通过 `GetRuntimeSetting` 得到当前的 `RuntimeSetting` 对象，修改相应的字段配置后，再通过 `UpdateRuntimeSetting` 使得配置生效。具体的可修改的字段值我们会在后续的文档中详细介绍。

下面是一个示例程序。在这个例子中通过修改 `RuntimeSetting` 中的 `barcodeFormatIds` 字段来配置DBR算法需要处理的码型。
```c++
CBarcodeReader* reader = new CBarcodeReader();   
reader->InitLicense("这里填入你的license");  
PublicRuntimeSettings* runtimeSettings = new PublicRuntimeSettings();   
reader->GetRuntimeSettings(runtimeSettings); //取出当前的模板参数  
runtimeSettings->barcodeFormatIds = BF_ALL ; //设置码型，这里设置BF_ALL，也就是所有barcodeFormatIds里的码型  
char sError[512];   
reader->UpdateRuntimeSettings(runtimeSettings, sError, 512); //更新模板参数  
reader->DecodeFile("这里填入你的文件路径", ""); //解码  
TextResultArray* paryResult = NULL;   
reader->GetAllTextResults(&paryResult); //拿出解码结果  
CBarcodeReader::FreeTextResults(&paryResult);   
delete runtimeSettings;   
delete reader;  
```
## DBR的 Json 模板
DBR 允许用户以配置文件的形式来管理参数，配置文件遵循 Json 语法。该方式适用于参数配置相对固定的情况。Json模板中主要涉及`ImageParameter`、 `FormatSpecification` 和 `RegionDefinition` 三个对象。   
`ImageParameter` 定义整张图片采用的全局配置。   
`FormatSpecification` 定义特定码型采用的配置。   
`RegionDefinition` 定义图像特定区域内的配置。   
下面我们详细来说明。
- ImageParameter   
`ImageParameter` 定义整张图片采用的全局配置。可以定义一个或多个。具体的可配置字段我们会在后续的文档详细介绍。   
定义一个 `ImageParameter` 时，可以在Json中通过  `ImageParameter` 这一key来指定。定义多个 `ImageParameter` 时，在Json中用 `ImageParameterArray` 这一key来指定，每一个`ImageParameter` 对象需要指定不同的 `Name`。   
若要使用Json模板中定义的 `ImageParameter` 配置， 首先我们需要用 `InitRuntimeSettingsWithFile` 载入一个Json文件，
或者利用 `InitRuntimeSettingsWithString` 载入一个 Json 字符串，然后在调用DBR解码函数的时候通过 `ImageParameter` 的 `Name` 来指定需要应用的具体配置。如果没有指定，则会使用DBR默认的 `ImageParameter` 配置对象。   
`InitRuntimeSettingsWithFile` 和 `InitRuntimeSettingsWithFile` 接口中的 `emSettingPriority` 参数用来指定载入Json配置时，对DBR的默认配置如何操作，若设 `CM_IGNORE`, 则不会改变默认配置， 如设为 `CM_OVERWRITE`，将逐个使用刚刚载入的 `ImageParameter` 配置对默认模板做merge操作。   
下面是示例的Json模板和程序。在这个例子中我们使用 `DecodeFile` 的参数  `PtemlateName` 来指定 `Name` 为 "IP1" 的 `ImageParameter`。   
```json
// 单个ImageParameter示例
{
    "Version": "3.0",
    "ImageParameter": {                   
        "Name": "IP1",
        "Description": "This is an imageParameter", 
        "BarcodeFormatIds": ["BF_ALL"]
     }
}

// 多个ImageParameter示例
{
    "Version": "3.0", 
    "ImageParameterArray": [                        
        {
            "Name": "IP1",              
            "BarcodeFormatIds": ["BF_ALL"]
        }, 
        {
            "Name": "IP2",                
            "BarcodeFormatIds": ["BF_CODE_39"]
        }, 
        {
            "Name": "IP3",                  
            "BarcodeFormatIds": ["BF_CODE_128"]
        }
    ]
}
```   
```c++
CBarcodeReader* reader = new CBarcodeReader();         
reader->InitLicense("这里填入license");        
int ret；  
char sError[512];         
ret = reader->InitRuntimeSettingsWithFile("JsonTemplate.json",CM_OVERWRITE,
sError,512); //通过Json文件路径载入一个模板配置  
reader->DecodeFile("这里填入文件路径", "ImageParameter1"); //使用Name为"IP1"的配置   
TextResultArray* paryResult = NULL;         
reader->GetAllTextResults(&paryResult); //拿出解码结果        
CBarcodeReader::FreeTextResults(&paryResult);         
delete runtimeSettings;         
delete reader;
```
- FormatSpecification   
如果用户仅仅想要对某一特定的码型进行某些参数的配置，那么应该使用 `FormatSpecification`。该对象定义某一具体码型采用的配置，如果配置和全局的
ImageParameter 配置不一致，那么 `FormatSpecification` 有更高的优先级。具体的可配置参数和适用场景参考我们的说明文档 [特定码型的配置参数]() 。   
在Json中，使用 `FormatSpecificationArray` 这一key来定义一个或多个
`FormatSpecification` 对象，通过定义不同的 `Name` 来区分。
使用 `FormatSpecificationNameArray` 这一key来指定若干 `FormatSpecification` 的 `Name` 来明确需要使用的 `FormatSpecification`。   
下面是一个示例。在这个例子中，我们定义了一个名为 “FS_1” 的 `FormatSpecification`，并使用了它。
```json
{
    "ImageParameter": {
        "Name": "ImageParameter1",
        "FormatSpecificationNameArray": ["FS_1"]
    }, 
    "FormatSpecificationArray": [
        {
            "Name": "FS_1",
            "AllmoduleDeviation": 10, 
            "BarcodeFormatIds": ["BF_CODE_39"]
        }
    ],
    "Version": "3.0"
}
```
- RegionDefinition  
如果你关心的区域只是图片上某一特定区域而非整张图片或者你想对图片的特定区域做额外配置，你应该使用 `RegionDefinition`。设置区域可以帮助 DBR 缩小要处理的图片范围，有利于提高速度。   
`RegionDefinition` 对象定义图像指定区域内的配置，如果该配置和全局的 `ImageParameter` 配置不一致，那么 `RegionDefinition` 有更高的优先级。具体可配置的参数参考我们关于 `RegionDefinition` 的 [详细说明文档]([1])。   
在Json中，用户通过 `RegionDefinitionArray` 来定义一个或多个 `RegionDefinition`，以不同的 `Name` 区分。
通过 `RegionDefinitionNameArray` 来明确使用哪些 `RegionDefinition`。   
下面是一个示例，该例子中，我们定义了2个 `RegionDefinition`，”RP_1” 和 “RP_2”，并使用了他们。
```json
{
    "ImageParameter": {
        "Name": "ImageParameter1",
        "Description": "This is a region template", 
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
            "MeasuredByPercentage": 1
        }, 
        {
            "Name": "RP_2",
            "BarcodeFormatIds": ["BF_CODE_93"]
        }
    ], 
    "Version": "3.0"
}

```

[1]: parameters-of-algorithm-flow\manually-define-region-of-interest.md



