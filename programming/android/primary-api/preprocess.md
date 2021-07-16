---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android API references - Filter Methods
description: This is the documentation - Android API references - Filter Methods page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android API references, Filter
needAutoGenerateSidebar: true
breadcrumbText: Android Filter Methods
---

# Android API Reference - Frame Preprocessing Methods

## AcquireListFrame

This API is designed for users to acquire a single frame. When this API is activated, it will fetch the latest frame from the DCE frame queue.

Java:

```java
    mCameraEnhancer.AcquireListFrame(true);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.AcquireListFrame(true)
```

## Fast Mode

This API is designed for users to setup DCE fast mode. DCE fast mode will cut frames into small images that contains barcode areas to improve decoding efficiency. It is recommended to be enabled when decoding single barcodes.

Java:

```java
    //To enable fast mode
    mCameraEnhancer.enableFastMode(true);
    //To get the value(status) of fast mode
    boolean x = mCameraEnhancer.getEnabledFastModeStatus();
```

Kotlin:

```kotlin
    //To enable fast mode
    mCameraEnhancer!!.enableFastMode(true)
    //To get the value(status) of fast mode
    var x:Boolean? = mCameraEnhancer!!.enabledFastModeStatus
```

## enableFrameFilter

Use `enableFrameFilter` to turn on/off frame filter.

Java:

```java
    mCameraEnhancer.enableFrameFilter(true);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.enableFrameFilter(true)
```

To check the status of frame filter mode, please use `getEnabledFrameFilterStatus`

Java:

```java
    boolean x = mCameraEnhancer.getEnabledFrameFilterStatus();
```

Kotlin:

```kotlin
    var x:Boolean? = mCameraEnhancer!!.enabledFrameFilterStatus
```

## setMaxFrameRate

Set max frame rate.

Java:

```java
    mCameraEnhancer.setMaxFrameRate(24);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setMaxFrameRate(24)
```

## enableSensorControl

Use `enableSensorControl` to turn on/off sensor control mode.

Java:

```java
    mCameraEnhancer.enableSensorControl(true);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.enableSensorControl(true)
```

To check the status of sensor control mode, please use `getEnabledSensorControlStatus`

Java:

```java
    boolean x = mCameraEnhancer.getEnabledSensorControlStatus();
```

Kotlin:

```kotlin
    var x:Boolean? = mCameraEnhancer!!.enabledSensorControlStatus
```

## setSensorControlThreshold

This API is designed for developers to apply different sensor sensitivity settings on different devices. The default value is 50.

Java:

```java
    mCameraEnhancer.setSensorControlThreshold(55);
```

Kotlin:

```kotlin
    mCameraEnhancer!!.setSensorControlThreshold(55)
```
