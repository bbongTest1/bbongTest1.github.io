---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android Release Note
description: This is the documentation - Android Release Note page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android Release Note
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: Android Release Note
---

# Release Note for Android

## 1.0.3 (07/20/2021)

### New

- Add Interface `CameraDLSLicenseVerificationListener` and callback `DLSLicenseVerificationCallback` to replace `CameraLTSLicenseVerificationListener` and `LTSLicenseVerificationCallback`.
- Added class `DMDLSConnectionParameters` to replace class `DMLTSConnectionParameters`.
- Added method `initLicenseFromDLS` in `CameraEnhancer` class to replace `initLicenseFromLTS`.

## 1.0.1 (06/10/2021)

### New

- Added a new property [`products`]({{ site.android-api-auxiliary }}lts-connection.html#products) in class `DMLTSConnectionParameters`.
- Added a new enumeration [`EnumProduct`]({{ site.enumerations }}enumproduct.html).

## 1.0 (04/29/2021)

- Video frame queue is available.
- Supports frame cropping mode.
- Supports regular camera control.
- Supports autofocus mode.
- Supports sensor control mode.
- Supports frame sharpness filter mode.
- Supports autozoom mode.
