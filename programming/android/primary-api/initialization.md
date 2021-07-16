---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android API references - CameraEnhancer Class
description: This is the documentation - Android API references - CameraEnhancer Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android API references, CameraEnhancer Class
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: Android CameraEnhancer Class
---

# Android CameraEnhancer Class

`com.dynamsoft.dce.CameraEnhancer` is the class that provides multifunctional APIs on frame preprocessing and camera controlling.

Java:

```java
CameraEnhancer mCameraEnhancer = new CameraEnhancer(MainActivity.this);
```

Kotlin:

```kotlin
mCameraEnhancer = CameraEnhancer(this@MainActivity)
```

## CameraEnhancer Methods

### [Frame preprocessing methods]({{site.android-api}}preprocess.html)

| Method | Description |
|--------|-------------|
| [`AcquireListFrame`]({{site.android-api}}preprocess.html#acquirelistframe) | Get the latest frame from the frame queue when this API is activated. |
| [`enableFastMode`]({{site.android-api}}preprocess.html#fast-mode) | Set true/false to turn on/off DCE fast mode. |
| [`getEnabledFastModeStatus`]({{site.android-api}}preprocess.html#fast-mode) | Get the current status of fast mode (on/off). |
| [`enableFrameFilter`]({{site.android-api}}preprocess.html#enableframefilter) | Set true/false to turn on/off DCE frame filter. |
| [`getEnabledFrameFilterStatus`]({{site.android-api}}preprocess.html#enableframefilter) | Get the status (on/off) of DCE frame filter mode. |
| [`setMaxFrameRate`]({{site.android-api}}preprocess.html#setmaxframerate) | Set max frame rate. |
| [`enableSensorControl`]({{site.android-api}}preprocess.html#enablesensorcontrol) | Set true/false to turn on/off DCE sensor control. |
| [`getEnabledSensorControlStatus`]({{site.android-api}}preprocess.html#enablesensorcontrol) | Get the status (on/off) of DCE sensor control mode. |
| [`setSensorControlThreshold`]({{site.android-api}}preprocess.html#setsensorcontrolthreshold) | Enable user to change sensor sensitivity (default value is 50). |

### [Regular camera methods]({{site.android-api}}camera.html)

| Method | Description |
|-----------------|---------------|
| [`getDeviceLevel`]({{site.android-api}}camera.html#getdevicelevel)| Make an evaluation on the current device and define its level for further use. |
| [`setAutoModeLevelParam`]({{site.android-api}}camera.html#setautomodelevelparam) | Set auto mode level parameter. |
| [`updateCameraSetting`]({{site.android-api}}camera.html#updatecamerasetting) | Update camera, filter and focus settings from Json. |
| [`getVersion`]({{site.android-api}}camera.html#getversion) | Check current DCE version |
| [`setCameraDesiredState`]({{site.android-api}}camera.html#camera-state) | Set Camera on/off. |
| [`getCameraDesiredState`]({{site.android-api}}camera.html#camera-state) | Get camera desired state. |
| [`getCameraCurrentState`]({{site.android-api}}camera.html#camera-state) | Get camera current state. |
| [`pauseCamera`]({{site.android-api}}camera.html#pausecamera-and-resumecamera) | Pause Camera. |
| [`resumeCamera`]({{site.android-api}}camera.html#pausecamera-and-resumecamera) | Resume Camera. |
| [`startScanning`]({{site.android-api}}camera.html#stopscanning-and-startscanning) | Start scanning. |
| [`stopScanning`]({{site.android-api}}camera.html#stopscanning-and-startscanning) | Stop scanning. |
| [`addCameraListener`]({{site.android-api}}camera.html#addcameralistener) | Add camera listener (on preview original, filtered or fast frames). |
| [`removeCameraListener`]({{site.android-api}}camera.html#addcameralistener) | Remove camera listener. |
| [`setTorchDesiredState`]({{site.android-api}}camera.html#torch-state) | Set torch state. |
| [`getTorchDesiredState`]({{site.android-api}}camera.html#torch-state) | Get torch desired state. |
| [`getTorchCurrentState`]({{site.android-api}}camera.html#torch-state) | Get torch current state. |
| [`addTorchListener`]({{site.android-api}}camera.html#addtorchlistener) | Add torch listener. |
| [`getCameraPosition`]({{site.android-api}}camera.html#camera-position) | Get current camera position. |
| [`switchCameraPosition`]({{site.android-api}}camera.html#camera-position) | Switch camera position front/back. |
| [`setResolution`]({{site.android-api}}camera.html#resolution-settings) | Set resolution. |
| [`getResolution`]({{site.android-api}}camera.html#resolution-settings) | Get current resolution setting. |
| [`getResolutionList`]({{site.android-api}}camera.html#resolution-settings) | Get all available resolutions |

### [Focus & zoom methods]({{site.android-api}}zoom-focus.html)

| Method | Description |
|-----------------|---------------|
| [`setAutoFocusPosition`]({{site.android-api}}zoom-focus.html#setautofocusposition) | Set auto focus position (Change the default auto focus position). |
| [`setManualFocusPosition`]({{site.android-api}}zoom-focus.html#setmanualfocusposition) | Set manual focus position (This focus position is only effected once for each time the API is called). |
| [`setFocalLength`]({{site.android-api}}zoom-focus.html#setfocallength) | Set focal length between 0 to 10 to enable fixed focal length mode. In fixed focal length mode, all focus parameters can't be changed until this mode is quit. To quit fixed focal length mode, please set focal length equals to -1. |
| [`enableDCEAutoFocus`]({{site.android-api}}zoom-focus.html#enabledceautofocus) | Set true/false to turn on/off DCE auto focus. |
| [`getEnabledDCEAutoFocusStatus`]({{site.android-api}}zoom-focus.html#enabledceautofocus) | Get the status (on/off) of DCE auto focus. |
| [`enableDefaultAutoFocus`]({{site.android-api}}zoom-focus.html#enabledefaultautofocus) | Set true/false to turn on/off default auto focus. |
| [`getEnabledDefaultAutoFocusStatus`]({{site.android-api}}zoom-focus.html#enabledefaultautofocus) | Get the status (on/off) of camera default auto focus. |
| [`enableRegularAutoFocus`]({{site.android-api}}zoom-focus.html#enableregularautofocus) | If this is true, camera will auto focus every 3 seconds. This focus mode will start automatically if DCE auto focus is enabled. Users can manually quit this focus mode when DCE auto focus is activated. |
| [`getEnabledRegularAutoFocusStatus`]({{site.android-api}}zoom-focus.html#enableregularautofocus) | Get the current status (on/off) of this auto focus mode. |
| [`setRegularAutoFocusParam`]({{site.android-api}}zoom-focus.html#setregularautofocusparam) | Set the time interval and terminate time for the regular auto focus |
| [`enableAutoFocusOnSharpnessChange`]({{site.android-api}}zoom-focus.html#enableautofocusonsharpnesschange) | If this is enabled, camera will autofocus when clarity change is detected. This focus mode will start automatically if DCE autofocus is enabled. Users can manually quit this focus mode when DCE autofocus is activated. |
| [`getEnabledAutoFocusOnSharpnessChangeStatus`]({{site.android-api}}zoom-focus.html#enableautofocusonsharpnesschange) | Get the current status (on/off) of this auto focus mode. |
| [`enableAutoZoom`]({{site.android-api}}zoom-focus.html#enableautozoom) | Set enableAutoZoom value true to enable auto zoom mode. |
| [`getEnabledAutoZoomStatus`]({{site.android-api}}zoom-focus.html#enableautozoom) | Get the status (on/off) of auto zoom mode. |
| [`setZoomFactor`]({{site.android-api}}zoom-focus.html#setzoomfactor) | Set zoom factor. |
