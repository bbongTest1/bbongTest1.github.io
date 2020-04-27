---
layout: manual-interface
id: interface_cpp
sourceCodeUrl: /dbr-detailed-info/manual/interface/c-and-cpp/cpp/index.md
---

# Dynamsoft Barcode Reader SDK - C++ API Reference

- [`CBarcodeReader` Methods](#cbarcodereader-methods) 
- [`CBarcodeReader` Attributes](#cbarcodereader-protected-attribute) 
- [Function Pointer](#function-pointer)
- [Error Code](#error-code)
- [Structs](#structs)  
- [Enumerations](#enumerations)

     
&nbsp; 


## CBarcodeReader Methods

### Constructor and Destructor
   
  | Method               | Description |
  |----------------------|-------------|
  | [`CBarcodeReader`](cpp-method/methods/constructor-and-destructor.md#cbarcodereader) | Default constructor of `CBarcodeReader` object.|
  | [`~CBarcodeReader`](cpp-method/methods/constructor-and-destructor.md#~cbarcodereader) | Destructor of `CBarcodeReader` object.|
   
   
&nbsp; 
   
   
### Decode
   
  | Method               | Description |
  |----------------------|-------------|
  | [`DecodeFile`](cpp-method/methods/decode.md#decodefile) | Decode barcodes from a specified image file. |
  | [`DecodeFileInMemory`](cpp-method/methods/decode.md#decodefileinmemory) | Decode barcodes from an image file in memory. |
  | [`DecodeBuffer`](cpp-method/methods/decode.md#decodebuffer) | Decode barcodes from raw buffer. |
  | [`DecodeBase64String`](cpp-method/methods/decode.md#decodebase64string) | Decode barcodes from a base64 encoded string. |
  | [`DecodeDIB`](cpp-method/methods/decode.md#decodedib) | Decode barcode from a handle of device-independent bitmap (DIB). |
   
   
&nbsp; 
   
   
   
### Parameter and Runtime Settings

#### Basic
   
  | Method               | Description |
  |----------------------|-------------|
  | [`SetModeArgument`](cpp-method/methods/parameter-and-runtime-settings-basic.md#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`GetModeArgument`](cpp-method/methods/parameter-and-runtime-settings-basic.md#getmodeargument) | Get argument value for the specified mode parameter. |
  | [`GetRuntimeSettings`](cpp-method/methods/parameter-and-runtime-settings-basic.md#getruntimesettings) | Get current runtime settings. |
  | [`UpdateRuntimeSettings`](cpp-method/methods/parameter-and-runtime-settings-basic.md#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`ResetRuntimeSettings`](cpp-method/methods/parameter-and-runtime-settings-basic.md#resetruntimesettings) | Reset runtime settings to default. |

#### Advanced
  
  | Method               | Description |
  |----------------------|-------------|
  | [`InitRuntimeSettingsWithFile`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)  | Initialize runtime settings with the settings in a given JSON file. |
  | [`InitRuntimeSettingsWithString`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`AppendTplFileToRuntimeSettings`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`AppendTplStringToRuntimeSettings`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`GetParameterTemplateCount`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#getparametertemplatecount) | Get the count of the parameter templates. |
  | [`GetParameterTemplateName`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#getparametertemplatename) | Get the parameter template name by index. |
  | [`OutputSettingsToFile`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`OutputSettingsToString`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#outputsettingstostring) | Output runtime settings to a string. |
  | [`OutputSettingsToStringPtr`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#outputsettingstostringptr) | Output runtime settings to a string. |
  | [`FreeSettingsString`](cpp-method/methods/parameter-and-runtime-settings-advanced.md#freesettingsstring) | Free memory allocated for runtime settings string. |
   
      
&nbsp; 

   
### License
  
  | Method               | Description |
  |----------------------|-------------|
  | [`InitLicense`](cpp-method/methods/license.md#initlicense) | Read product key and activate the SDK. |
  | [`InitLicenseFromServer`](cpp-method/methods/license.md#initlicensefromserver) | Initialize license and connect to the specified server for online verification. |
  | [`InitLicenseFromLicenseContent`](cpp-method/methods/license.md#initlicensefromlicensecontent) | Initialize license from the license content on client machine for offline verification. |
  | [`OutputLicenseToString`](cpp-method/methods/license.md#outputlicensetostring) | Output the license content to a string from the license server. |
  | [`OutputLicenseToStringPtr`](cpp-method/methods/license.md#outputlicensetostringptr) | Output the license content to a string from the license server. |
  | [`FreeLicenseString`](cpp-method/methods/license.md#freelicensestring) | Free memory allocated for the license string. |
   
   
&nbsp; 
   
   
### Result
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetAllTextResults`](cpp-method/methods/result.md#getalltextresults) | Get all recognized barcode results. |
  | [`FreeTextResults`](cpp-method/methods/result.md#freetextresults) | Free memory allocated for text results. |
  | [`GetIntermediateResults`](cpp-method/methods/result.md#getintermediateresults) | Get intermediate results. |
  | [`FreeIntermediateResults`](cpp-method/methods/result.md#freeintermediateresults) | Free memory allocated for the intermediate results. |
   
      
&nbsp; 

   
### Status Retrieval
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetErrorString`](cpp-method/methods/status-retrieval.md#geterrorstring) | Get error message by error code.|
  | [`GetVersion`](cpp-method/methods/status-retrieval.md#getversion) | Get version information of SDK.|
   
      
&nbsp; 

   
### Video

#### Decode
    
   | Method               | Description |
   |----------------------|-------------|
   | [`StartFrameDecoding`](cpp-method/methods/video.md#startframedecoding) | Decode barcodes from inner frame queue. |
   | [`StartFrameDecodingEx`](cpp-method/methods/video.md#startframedecodingex) | Decode barcodes from inner frame queue. |
   | [`AppendFrame`](cpp-method/methods/video.md#appendframe) | Append a frame image buffer to the inner frame queue. |
   | [`StopFrameDecoding`](cpp-method/methods/video.md#stopframedecoding) | Stop thread used for frame decoding. |

#### Parameter
   
   | Method               | Description |
   |----------------------|-------------|
   | [`InitFrameDecodingParameters`](cpp-method/methods/video.md#initframedecodingparameters) | Initialize frame decoding parameter. |

#### Callback
   
   | Method               | Description |
   |----------------------|-------------|
   | [`SetErrorCallback`](cpp-method/methods/video.md#seterrorcallback) | Set callback function to process errors generated during frame decoding. |
   | [`SetTextResultCallback`](cpp-method/methods/video.md#settextresultcallback) | Set callback function to process text results generated during frame decoding. |
   | [`SetIntermediateResultCallback`](cpp-method/methods/video.md#setintermediateresultcallback) | Set callback function to process intermediate results generated during frame decoding. |

#### Status retrieval
   
   | Method               | Description |
   |----------------------|-------------|
   | [`GetLengthOfFrameQueue`](cpp-method/methods/video.md#getlengthofframequeue) | Get length of current inner frame queue. |
 
   
&nbsp; 


## `CBarcodeReader` Protected Attribute
  
  | Attribute            | Description |
  |----------------------|-------------|
  | [`m_pBarcodeReader`](cpp-method/attribute/m_pBarcodeReader.md)  | |
  
   
&nbsp; 

## Function Pointer

  | Function | Description |
  |----------|-------------|
  | [`CB_Error`](cpp-method/function-pointer.md#cb_error) | Represents the method that will handle the error code returned by the SDK. |
  | [`CB_IntermediateResult`](cpp-method/function-pointer.md#cb_intermediateresult) | Represents the method that will handle the intermediate result array returned by the SDK. |
  | [`CB_TextResult`](cpp-method/function-pointer.md#cb_textresult) | Represents the method that will handle the text result array returned by the SDK. | 

&nbsp;


## [Error Code]({{ site.enumerations }}error-code.html)
		

&nbsp;

## [Structs](struct-glossary.md)
- [`AztecDetails`](struct/AztecDetails.html)	
- [`Contour`](struct/Contour.html)	
- [`DBRPoint`](struct/DBRPoint.html)	
- [`DataMatrixDetails`](struct/DataMatrixDetails.html)		
- [`ExtendedResult`](struct/ExtendedResult.html)		
- [`FrameDecodingParameters`](struct/FrameDecodingParameters.html)	
- [`FurtherModes`](struct/FurtherModes.html)		
- [`ImageData`](struct/ImageData.html)		
- [`IntermediateResult`](struct/IntermediateResult.html)		
- [`IntermediateResultArray`](struct/IntermediateResultArray.html)		
- [`LineSegment`](struct/LineSegment.html)		
- [`LocalizationResult`](struct/LocalizationResult.html)		
- [`OneDCodeDetails`](struct/OneDCodeDetails.html)		
- [`PDF417Details`](struct/PDF417Details.html)		
- [`PublicRuntimeSettings`](struct/PublicRuntimeSettings.html)		
- [`QRCodeDetails`](struct/QRCodeDetails.html)
- [`Quadrilateral`](struct/Quadrilateral.md)
- [`RegionDefinition`](struct/RegionDefinition.html)		
- [`RegionOfInterest`](struct/RegionOfInterest.html)		
- [`SamplingImageData`](struct/SamplingImageData.html)		
- [`TextResult`](struct/TextResult.html)		
- [`TextResultArray`](struct/TextResultArray.html)	


&nbsp; 


## [Enumerations]({{ site.parameters_reference }}enum-glossary.html)
- [`AccompanyingTextRecognitionMode`]({{ site.enumerations }}parameter-mode-enums.html#accompanyingtextrecognitionmode)	
- [`BarcodeColourMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecolourmode)	
- [`BarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode)	
- [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)	
- [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)	
- [`BinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode)
- [`ClarityCalculationMethod`]({{ site.enumerations }}frame-decoding.html#claritycalculationmethod) 
- [`ClarityFilterMode`]({{ site.enumerations }}frame-decoding.html#clarityfiltermode) 
- [`ColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode)	
- [`ColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode)	
- [`ConflictMode`]({{ site.enumerations }}parameter-mode-enums.html#conflictmode)	
- [`DeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode)	
- [`DPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode)	
- [`GrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode)	
- [`ImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat)	
- [`ImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode)	
- [`IMResultDataType`]({{ site.enumerations }}result-enums.html#imresultdatatype)	
- [`IntermediateResultSavingMode`]({{ site.enumerations }}result-enums.html#intermediateresultsavingmode)	
- [`IntermediateResultType`]({{ site.enumerations }}result-enums.html#intermediateresulttype)	
- [`LocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode)
- [`PDFReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#pdfreadingmode)   
- [`QRCodeErrorCorrectionLevel`]({{ site.enumerations }}other-enums.html#qrcodeerrorcorrectionlevel)	
- [`RegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode)	
- [`ResultCoordinateType`]({{ site.enumerations }}result-enums.html#resultcoordinatetype)	
- [`ResultType`]({{ site.enumerations }}result-enums.html#resulttype)	
- [`ScaleUpMode`]({{ site.enumerations }}parameter-mode-enums.html#scaleupmode)	
- [`TerminatePhase`]({{ site.enumerations }}parameter-mode-enums.html#terminatephase)	
- [`TextAssistedCorrectionMode`]({{ site.enumerations }}parameter-mode-enums.html#textassistedcorrectionmode)	
- [`TextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode)	
- [`TextResultOrderMode`]({{ site.enumerations }}result-enums.html#textresultordermode)	
- [`TextureDetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#texturedetectionmode)