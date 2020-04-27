---
layout: default-layout
sideHeader: C and C++ Struct
sourceCodeUrl: programming/c-cplusplus/api-reference/struct/ExtendedResult.md
sidebarListFile: sidelist-c-cpp-structs
needCollapsedSideBar: false
needAutoGenerateSidebar: false
---


# ExtendedResult
Stores the extended result. 

## Typedefs

```cpp
typedef struct tagExtendedResult  ExtendedResult
typedef struct tagExtendedResult*  PExtendedResult
```  

---

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`resultType`](#resulttype) | [`ResultType`]({{ site.enumerations }}ResultType.html) |
| [`barcodeFormat`](#barcodeformat) | [`BarcodeFormat`]({{ site.enumerations }}BarcodeFormat.html) |
| [`barcodeFormatString`](#barcodeformatstring) | *const char \** |
| [`barcodeFormat_2`](#barcodeformat_2) | [`BarcodeFormat_2`]({{ site.enumerations }}BarcodeFormat_2.html) |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *const char \** | 
| [`confidence`](#confidence) | *int* | 
| [`bytes`](#bytes) | *unsigned char \** | 
| [`bytesLength`](#byteslength) | *int* | 
| [`accompanyingTextBytes`](#accompanyingtextbytes) | *unsigned char \** | 
| [`accompanyingTextBytesLength`](#accompanyingtextbyteslength) | *int* | 
| [`deformation`](#deformation) | *int* | 
| [`detailedResult`](#detailedresult) | *void \** |
| [`samplingImage`](#samplingimage) | [`SamplingImageData`](SamplingImageData.md) |
| [`clarity`](#clarity) | *int* | 
| [`reserved`](#reserved) | *char\[40\]* | 

### resultType
Extended result type. 
```cpp
ResultType tagExtendedResult::resultType
```

### barcodeFormat
Barcode type in BarcodeFormat group 1. 
```cpp
BarcodeFormat tagExtendedResult::barcodeFormat
```

### barcodeFormatString
Barcode type in BarcodeFormat group 1 as string.
```cpp
const char* tagExtendedResult::barcodeFormatString
```

### barcodeFormat_2
Barcode type in BarcodeFormat group 2.
```cpp
BarcodeFormat_2 tagExtendedResult::barcodeFormat_2
```
 
### barcodeFormatString_2
Barcode type in BarcodeFormat group 2 as string.
```cpp
const char* tagExtendedResult::barcodeFormatString_2
```

### confidence
The confidence of the result.
```cpp
int tagExtendedResult::confidence
```

### bytes
The content in a byte array.
```cpp
unsigned char* tagExtendedResult::bytes
```

### bytesLength
The length of the byte array.
```cpp
int tagExtendedResult::bytesLength
```

### accompanyingTextBytes
The accompanying text content in a byte array.
```cpp
unsigned char* tagExtendedResult::accompanyingTextBytes
```

### accompanyingTextBytesLength
The length of the accompanying text byte array.
```cpp
int tagExtendedResult::accompanyingTextBytesLength
```

### deformation
The deformation value.
```cpp
int tagExtendedResult::deformation
```

### detailedResult
One of the following: [`QRCodeDetails`](QRCodeDetails.md), [`PDF417Details`](PDF417Details.md), [`DataMatrixDetails`](DataMatrixDetails.md), [`AztecDetails`](AztecDetails.md), [`OneDCodeDetails`](OneDCodeDetails.md).
```cpp
void* tagExtendedResult::detailedResult
```

### samplingImage
The sampling image info.
```cpp
SamplingImageData tagExtendedResult::samplingImage
```
 
### clarity
The clarity of the barcode zone in percentage.
```cpp
int tagExtendedResult::clarity
```

### reserved
Reserved memory for struct. The length of this array indicates the size of the memory reserved for this struct.
```cpp
char tagExtendedResult::reserved[40]
```
