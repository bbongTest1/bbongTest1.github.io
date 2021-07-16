---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android API references - Regular Camera Methods
description: This is the documentation - Android API references - Basic Settings page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android API references, Regular Camera Methods
needAutoGenerateSidebar: true
breadcrumbText: Android Regular Camera Methods
---

# Android API Reference - Regular Camera Methods

## getDeviceLevel

This API can help you make an evaluation on your mobile device. It will be helpful to automatically turn off DCE on high-level mobile devices.

Java:

```java
    mCameraEnhancer.getDeviceLevel();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.deviceLevel
```

## setAutoModeLevelParam

Set auto mode level parameter - cpuMHz1, cpuMHz2, ramMB1, ramMB2. These are settings for device-level.

| CPU & RAM | If device CPUMHz > cpuMHz2 | If device CPUMHz1 < CPUMHz < cpuMHz2 | If device CPUMHz < CPUMHz1 |
|--|--|--|--|
| If device ramMB > ramMB2 | Device-level is high | Device-level is mid | Device-level is mid |
| If device ramMB1 < ramMB < ramMB2 | Device-level is mid | Device-level is mid | Device-level is mid |
| If device ramMB < ramMB1 | Device-level is mid | Device-level is mid | Device-level is low |

Java:

```java
    mCameraEnhancer.setAutoModeLevelParam(cpuMHz1,cpuMHz2,ramMB1,ramMB2);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setAutoModeLevelParam(cpuMHz1,cpuMHz2,ramMB1,ramMB2)
```

## updateCameraSetting

There are some detailed settings that can be updated from JSON.

To update from JSON string:

Java:

```java
    mCameraEnhancer.updateCameraSetting("{"sensorvalue":3,"graydiffthreshold":30,"conversioncountthreshold":30,"sharpnessthreshold":0.2,"sharpnessthresholdlarge":0.4,"abssharpnessthreshold":200,"absgraythreshold":35,"claritythreshold":0.1}");
```

Kotlin:

```kotlin
    mCameraEnhancer!!.updateCameraSetting("{'sensorvalue':3,'graydiffthreshold':30,'conversioncountthreshold':30,'sharpnessthreshold':0.2,'sharpnessthresholdlarge':0.4,'abssharpnessthreshold':200,'absgraythreshold':35,'claritythreshold':0.1}")
```

To update from JSON file:

Java:

```java
    mCameraEnhancer.updateCameraSetting("Your file path here.");
```

Kotlin:

```kotlin
    mCameraEnhancer!!.updateCameraSetting("Your file path here.")
```

JSON file template:

```json
    {
        //Absolute sharpness value, A threshold value for controlling filter
        "abssharpnessthreshold":200,
        //Sensor value, A threshold value for controlling filter
        "sensorvalue":3,        
        //A threshold value for gray scale analysis
        "graydiffthreshold":30,
        //A threshold for judging whether the device is shaking
        "sharpnessthreshold":0.2,
        //A threshold for judging whether the device is shaking violently
        "sharpnessthresholdlarge":0.4,
        //A threshold value for calculating sharpness
        "absgraythreshold":35,
        //A threshold value for controlling auto zoom
        "conversioncountthreshold":30,
        //A threshold value that controlling auto focus
        "claritythreshold":0.1
    }
```

## getVersion

Users can check the current DCE version by using this API.

Java:

```java
    mCameraEnhancer.getVersion();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.version
```

## Camera State

Get the current camera status (on/off).

Java:

```java
    mCameraEnhancer.getCameraCurrentState();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.cameraCurrentState
```

Get the cameras desired status (on/off).

Java:

```java
    mCameraEnhancer.getCameraDesireState();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.cameraDesireState
```

Use `CameraState.CAMERA_STATE_ON` to set the camera on and use `CameraState.CAMERA_STATE_OFF` to set it off.

Java:

```java
    mCameraEnhancer.setCameraDesireState(CameraState.CAMERA_STATE_OFF);
    mCameraEnhancer.setCameraDesireState(CameraState.CAMERA_STATE_ON);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setCameraDesiredState(CameraState.CAMERA_STATE_ON)
    mCameraEnhancer!!.setCameraDesiredState(CameraState.CAMERA_STATE_OFF)
```

## pauseCamera and resumeCamera

Note: these APIs are created for pausing & resuming the camera but the camera module will still be working when paused. If you want to shut down the camera module please use `stopScanning`.

Java:

```java
    mCameraEnhancer.pauseCamera();
    mCameraEnhancer.resumeCamera();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.pauseCamera()
    mCameraEnhancer!!.resumeCamera()
```

## stopScanning and startScanning

Control the stopping & starting of the camera module.

Java:

```java
    mCameraEnhancer.startScanning();
    mCameraEnhancer.stopScanning();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.startScanning()
    mCameraEnhancer!!.stopScanning()
```

## addCameraListener

Add Camera Listener

Java:

```java
    mCameraEnhancer.addCameraListener(new CameraListener() {
        @Override
        public void onPreviewOriginalFrame(Frame frame) {

        }
        @Override
        public void onPreviewFilterFrame(Frame frame) {

        }

        @Override
        public void onPreviewFastFrame(Frame frame) {

        }
    });
```

Kotlin:

```kotlin
    mCameraEnhancer!!.addCameraListener(object : CameraListener {
        override fun onPreviewOriginalFrame(frame: Frame) {}
        override fun onPreviewFilterFrame(frame: Frame) {}
        override fun onPreviewFastFrame(frame: Frame) {}
    })
```

Remove Camera Listener

Java:

```java
    mCameraEnhancer.removeCameraListener();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.removeCameraListener()
```

## Torch State

Get current torch state (on/off)

Java:

```java

    mCameraEnhancer.getTorchCurrentState();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.removeCameraListener()
```

Get desired torch state (on/off)

Java:

```java
    mCameraEnhancer.getTorchDesiredState();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.torchDesiredState
```

Use `TorchState.TORCH_STATE_ON` to set the torch on and use `TorchState.TORCH_STATE_OFF` to set it off.

Java:

```java
    mCameraEnhancer.setTorchDesiredState(TorchState.TORCH_STATE_AUTO);
    mCameraEnhancer.setTorchDesiredState(TorchState.TORCH_STATE_ON);
    mCameraEnhancer.setTorchDesiredState(TorchState.TORCH_STATE_OFF);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setTorchDesiredState(TorchState.TORCH_STATE_AUTO)
    mCameraEnhancer!!.setTorchDesiredState(TorchState.TORCH_STATE_ON)
    mCameraEnhancer!!.setTorchDesiredState(TorchState.TORCH_STATE_OFF)
```

## addTorchListener

Java:

```java
    mCameraEnhancer.addTorchListener(new TorchListener() {
        @Override
        public void onTorchStateChanged(TorchState torchState) {
                
        }
    });
```

Kotlin:

```kotlin
    mCameraEnhancer!!.addTorchListener(object : TorchListener {
        override fun onTorchStateChanged(TorchState: torchState) {}
    })
```

## Camera Position

DCE will use the back camera of your mobile device by default. You can use `getCameraPosition` to check which camera is activated and use `switchCameraPosition` to change the setting.
To get camera position:

Java:

```java
    mCameraEnhancer.getCameraPosition();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.cameraPosition
```

To change settings, use `CameraPosition.CAMERA_POSITION_USER` to activate front camera and use `CameraPosition.CAMERA_POSITION_WORLD` to activate back camera

Java:

```java
    mCameraEnhancer.switchCameraPosition(CameraPosition.CAMERA_POSITION_USER);
    mCameraEnhancer.switchCameraPosition(CameraPosition.CAMERA_POSITION_WORLD);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.switchCameraPosition(CameraPosition.CAMERA_POSITION_USER)
    mCameraEnhancer!!.switchCameraPosition(CameraPosition.CAMERA_POSITION_WORLD)
```

## Resolution Settings

These APIs are created for you to get or change camera resolution settings.

Java:

```java
    mCameraEnhancer.getResolution();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.resolution
```

Camera resolution parameters can be viewed in [`parameter-resolution`]({{site.reference}}#Resolution). If the resolution setting is not available on the device, the device will run the closest resolution to the chosen resolution.

Java:

```java
    mCameraEnhancer.setResolution(Resolution.RESOLUTION_1080P);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setResolution(Resolution.RESOLUTION_1080P)
```

Get all available resolutions that can be set to the current camera.

Java:

```java
    mCameraEnhancer.getResolutionList();
```

Kotlin:

```kotlin
    mCameraEnhancer!!.resolutionList
```
