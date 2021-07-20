---
layout: default-layout
title: Dynamsoft Camera Enhancer - iOS Release Note
description: This is the documentation - iOS Release Note page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, iOS Release Note
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: iOS Release Note
---

# Release Note for iOS

## 1.0.3 (07/20/2021)

### New

- Add Interface `CameraDLSLicenseVerificationListener` and callback `DLSLicenseVerificationCallback` to replace `CameraLTSLicenseVerificationListener` and `LTSLicenseVerificationCallback`.
- Added class `DCEDLSConnectionParameters` to replace class `DCELTSConnectionParameters`.
- Added method `initLicenseFromDLS` in `CameraEnhancer` class to replace `initLicenseFromLTS`.

## 1.0.1 (06/10/2021)

### Update

- Class `iDMLTSConnectionParameters` is renamed to [`iDCELTSConnectionParameters`]({{ site.ios-api-auxiliary }}ltsconnection.html)

### New

- Added a new property [`products`]({{ site.ios-api-auxiliary }}ltsconnection.html#products) in class `iDCELTSConnectionParameters`.
- Added a new enumeration [`EnumProduct`]({{ site.enumerations }}enumproduct.html).

## 1.0 (04/29/2021)

- Video frame queue is available.
- Supports frame cropping mode.
- Supports regular camera control.
- Supports autofocus mode.
- Supports sensor control mode.
- Supports frame sharpness filter mode.
- Supports autozoom mode.
