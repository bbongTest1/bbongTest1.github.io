---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android CameraView Class
description: This is the documentation - Android CameraView Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android, CameraView
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: Android CameraView Class
---

# com.dynamsoft.dce.CameraView

This page is for `CameraView` Class. `CameraView` is designed to Make basic settings on the overlay.

```java
CameraView cameraView;
mCameraEnhancer.addCameraView(cameraView);
```

| Method Name | Description |
|------|------|
| [`addOverlay`](#addoverlay) | Add overlay |
| [`removeOverlay`](#removeoverlay) | Remove overlay |
| [`setBrushColor`](#setbrushcolor) | Set the brush color |

## addOverlay

Java:

```java
cameraView.addOverlay();
```

Kotlin:

```kotlin
cameraView!!.addOverlay()
```

## removeOverlay

Java:

```java
cameraView.removeOverlay();
```

Kotlin:

```kotlin
cameraView!!.removeOverlay()
```

## setBrushColor

Java:

```java
cameraView.setBrushColor("Put your color string here");
```

Kotlin:

```kotlin
cameraView!!.setBrushColor("Put your color string here")
```
