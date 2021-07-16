---
layout: default-layout
title: Dynamsoft Camera Enhancer - Objective-C & Swift API references - Frame Preprocessing Methods
description: This is the documentation - Objective-C & Swift API references - Frame Preprocessing Methods page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Objective-C & Swift, API references, Frame Preprocessing Methods
needAutoGenerateSidebar: true
breadcrumbText: iOS Frame Preprocessing Methods
---

# iOS API Reference - Frame Preprocessing Methods

## acquireListFrame

This API is designed for users to acquire a single frame. When this API is activated, it will fetch the latest frame from the DCE frame queue.

Objective-C:

```objectivec
    FramePackage *fg = [self.camera AcquireListFrame];
```

Swift:

```swift
    let fg = self.dce.acquireListFrame() 
```

## enableFastMode

This API is designed for users to setup DCE fast mode. DCE fast mode will cut frames into small images that contains barcode areas to improve decode efficiency. It is recommended to be enabled when decoding a single barcode.

Objective-C:

```objectivec
    [dce enableFastMode:true];
    //To check the status of DCE fast mode
    [dce getEnableFastMode];
```

Swift:

```swift
    dce.enableFastMode = true
```

## enableSensorControl

Turn on (off) sensor control

Objective-C:

```objectivec
    [dce enableSensorControl:true];
    //To check the status of the DCE sensor control
    BOOL res= [dce enableSensorControl];
```

Swift:

```swift
    dce.enableSensorControl(true)
    //To check the status of the DCE sensor control
    let res = dce.enableSensorControl
```

## setSensorControlThreshold

This API is designed for developers to apply different sensor sensitivity settings on different devices. The default value is 50.

Objective-C:

```objectivec
    [dce setSensorControlThreshold:55];
```

Swift:

```swift
    dce.setSensorControlThreshold(55)
```

## enableFrameFilter

Turn on(off) DCE filter (recommended to be true).

Objective-C:

```objectivec
    [dce enableFrameFilter:true];
    //To check the status of the DCE frame filter
    BOOL res= [dce enableFrameFilter];
```

Swift:

```swift
    dce.enableFrameFilter(true)
    //To check the status of the DCE frame filter
    let res = dce.enableFrameFilter
```

## setMaxFrameRate

Set max frame rate.

Objective-C:

```objectivec
    [dce setMaxFrameRate:24];
```

Swift:

```swift
    dce.setMaxFrameRate(24)
```
