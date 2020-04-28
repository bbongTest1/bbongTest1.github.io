---
layout: default-layout
sideHeader: C++ API
sourceCodeUrl: /programming/c-cplusplus/api-referecnde/cpp-api/index.md
sidebarListFile: sidelist-c-cpp
needCollapsedSideBar: false
needAutoGenerateSidebar: false
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
  | [`CBarcodeReader`](constructor-and-destructor.md#cbarcodereader) | Default constructor of `CBarcodeReader` object.|
  | [`~CBarcodeReader`](constructor-and-destructor.md#~cbarcodereader) | Destructor of `CBarcodeReader` object.|
   
   
&nbsp; 
   
   
### Decode
   
  | Method               | Description |
  |----------------------|-------------|
  | [`DecodeFile`](decode.md#decodefile) | Decode barcodes from a specified image file. |
  | [`DecodeFileInMemory`](decode.md#decodefileinmemory) | Decode barcodes from an image file in memory. |
  | [`DecodeBuffer`](decode.md#decodebuffer) | Decode barcodes from raw buffer. |
  | [`DecodeBase64String`](decode.md#decodebase64string) | Decode barcodes from a base64 encoded string. |
  | [`DecodeDIB`](decode.md#decodedib) | Decode barcode from a handle of device-independent bitmap (DIB). |
   
   
&nbsp; 
   
   
   
### Parameter and Runtime Settings

#### Basic
   
  | Method               | Description |
  |----------------------|-------------|
  | [`SetModeArgument`](parameter-and-runtime-settings-basic.md#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`GetModeArgument`](parameter-and-runtime-settings-basic.md#getmodeargument) | Get argument value for the specified mode parameter. |
  | [`GetRuntimeSettings`](parameter-and-runtime-settings-basic.md#getruntimesettings) | Get current runtime settings. |
  | [`UpdateRuntimeSettings`](parameter-and-runtime-settings-basic.md#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`ResetRuntimeSettings`](parameter-and-runtime-settings-basic.md#resetruntimesettings) | Reset runtime settings to default. |

#### Advanced
  
  | Method               | Description |
  |----------------------|-------------|
  | [`InitRuntimeSettingsWithFile`](parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)  | Initialize runtime settings with the settings in a given JSON file. |
  | [`InitRuntimeSettingsWithString`](parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`AppendTplFileToRuntimeSettings`](parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`AppendTplStringToRuntimeSettings`](parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`GetParameterTemplateCount`](parameter-and-runtime-settings-advanced.md#getparametertemplatecount) | Get the count of the parameter templates. |
  | [`GetParameterTemplateName`](parameter-and-runtime-settings-advanced.md#getparametertemplatename) | Get the parameter template name by index. |
  | [`OutputSettingsToFile`](parameter-and-runtime-settings-advanced.md#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`OutputSettingsToString`](parameter-and-runtime-settings-advanced.md#outputsettingstostring) | Output runtime settings to a string. |
  | [`OutputSettingsToStringPtr`](parameter-and-runtime-settings-advanced.md#outputsettingstostringptr) | Output runtime settings to a string. |
  | [`FreeSettingsString`](parameter-and-runtime-settings-advanced.md#freesettingsstring) | Free memory allocated for runtime settings string. |
   
      
&nbsp; 

   
### License
  
  | Method               | Description |
  |----------------------|-------------|
  | [`InitLicense`](license.md#initlicense) | Read product key and activate the SDK. |
  | [`InitLicenseFromServer`](license.md#initlicensefromserver) | Initialize license and connect to the specified server for online verification. |
  | [`InitLicenseFromLicenseContent`](license.md#initlicensefromlicensecontent) | Initialize license from the license content on client machine for offline verification. |
  | [`OutputLicenseToString`](license.md#outputlicensetostring) | Output the license content to a string from the license server. |
  | [`OutputLicenseToStringPtr`](license.md#outputlicensetostringptr) | Output the license content to a string from the license server. |
  | [`FreeLicenseString`](license.md#freelicensestring) | Free memory allocated for the license string. |
   
   
&nbsp; 
   
   
### Result
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetAllTextResults`](result.md#getalltextresults) | Get all recognized barcode results. |
  | [`FreeTextResults`](result.md#freetextresults) | Free memory allocated for text results. |
  | [`GetIntermediateResults`](result.md#getintermediateresults) | Get intermediate results. |
  | [`FreeIntermediateResults`](result.md#freeintermediateresults) | Free memory allocated for the intermediate results. |
   
      
&nbsp; 

   
### Status Retrieval
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetErrorString`](status-retrieval.md#geterrorstring) | Get error message by error code.|
  | [`GetVersion`](status-retrieval.md#getversion) | Get version information of SDK.|
   
      
&nbsp; 

   
### Video

#### Decode
    
   | Method               | Description |
   |----------------------|-------------|
   | [`StartFrameDecoding`](video.md#startframedecoding) | Decode barcodes from inner frame queue. |
   | [`StartFrameDecodingEx`](video.md#startframedecodingex) | Decode barcodes from inner frame queue. |
   | [`AppendFrame`](video.md#appendframe) | Append a frame image buffer to the inner frame queue. |
   | [`StopFrameDecoding`](video.md#stopframedecoding) | Stop thread used for frame decoding. |

#### Parameter
   
   | Method               | Description |
   |----------------------|-------------|
   | [`InitFrameDecodingParameters`](video.md#initframedecodingparameters) | Initialize frame decoding parameter. |

#### Callback
   
   | Method               | Description |
   |----------------------|-------------|
   | [`SetErrorCallback`](video.md#seterrorcallback) | Set callback function to process errors generated during frame decoding. |
   | [`SetTextResultCallback`](video.md#settextresultcallback) | Set callback function to process text results generated during frame decoding. |
   | [`SetIntermediateResultCallback`](video.md#setintermediateresultcallback) | Set callback function to process intermediate results generated during frame decoding. |

#### Status retrieval
   
   | Method               | Description |
   |----------------------|-------------|
   | [`GetLengthOfFrameQueue`](video.md#getlengthofframequeue) | Get length of current inner frame queue. |
 
   
&nbsp; 


## `CBarcodeReader` Protected Attribute
  
  | Attribute            | Description |
  |----------------------|-------------|
  | [`m_pBarcodeReader`]()  | |
  
   
&nbsp; 

## Function Pointer

  | Function | Description |
  |----------|-------------|
  | [`CB_Error`](function-pointer.md#cb_error) | Represents the method that will handle the error code returned by the SDK. |
  | [`CB_IntermediateResult`](function-pointer.md#cb_intermediateresult) | Represents the method that will handle the intermediate result array returned by the SDK. |
  | [`CB_TextResult`](function-pointer.md#cb_textresult) | Represents the method that will handle the text result array returned by the SDK. | 

&nbsp;


## [Error Code]({{ site.enumerations }}error-code.html)
		

&nbsp;

## [Structs]({{ site.structs }})
- [`AztecDetails`]({{ site.structs }}AztecDetails.html)	
- [`Contour`]({{ site.structs }}Contour.html)	
- [`DBRPoint`]({{ site.structs }}DBRPoint.html)	
- [`DataMatrixDetails`]({{ site.structs }}DataMatrixDetails.html)		
- [`ExtendedResult`]({{ site.structs }}ExtendedResult.html)		
- [`FrameDecodingParameters`]({{ site.structs }}FrameDecodingParameters.html)	
- [`FurtherModes`]({{ site.structs }}FurtherModes.html)		
- [`ImageData`]({{ site.structs }}ImageData.html)		
- [`IntermediateResult`]({{ site.structs }}IntermediateResult.html)		
- [`IntermediateResultArray`]({{ site.structs }}IntermediateResultArray.html)		
- [`LineSegment`]({{ site.structs }}LineSegment.html)		
- [`LocalizationResult`]({{ site.structs }}LocalizationResult.html)		
- [`OneDCodeDetails`]({{ site.structs }}OneDCodeDetails.html)		
- [`PDF417Details`]({{ site.structs }}PDF417Details.html)		
- [`PublicRuntimeSettings`]({{ site.structs }}PublicRuntimeSettings.html)		
- [`QRCodeDetails`]({{ site.structs }}QRCodeDetails.html)
- [`Quadrilateral`]({{ site.structs }}Quadrilateral.md)
- [`RegionDefinition`]({{ site.structs }}RegionDefinition.html)		
- [`RegionOfInterest`]({{ site.structs }}RegionOfInterest.html)		
- [`SamplingImageData`]({{ site.structs }}SamplingImageData.html)		
- [`TextResult`]({{ site.structs }}TextResult.html)		
- [`TextResultArray`]({{ site.structs }}TextResultArray.html)	


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