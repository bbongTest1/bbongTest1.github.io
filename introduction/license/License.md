---
layout: default-layout
title: Dynamsoft Camera Enhancer - License initialization
description: This is the documentation - License initialization page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, License initialization
needAutoGenerateSidebar: true
breadcrumbText: License Initialization
---
# License initialization

## Get a trial key

- A 7-day public trial key is available for every new device for first use of Dynamsoft Camera Enhancer.
- If your free key is expired, please visit <a href="https://www.dynamsoft.com/customer/license/trialLicense?product=dce&utm_source=docs&package=android" target="_blank">Private Trial License Page</a> to get a 30-day extension.

## Get a full key license

- [Please contact us to purchase for full key license]({{site.contact-us}})

## Set up the license from Dynamsoft License Server

Once you have a license you can use following code to set up your license from `Dynamsoft License Server`:

For Android users:

Android sample

Java:

```java
    DMDLSConnectionParameters info = new DMDLSConnectionParameters();
    info.organizationID = "Your organizationID";
    mCamera.initLicenseFromDLS(info, new CameraDLSLicenseVerificationListener() {
        @Override
        public void DLSLicenseVerificationCallback(boolean b, Exception e) {
            if(!b && e != null){
                e.printStackTrace();
            }
        }
    });
```

Kotlin:

```kotlin
    val info = com.dynamsoft.dce.DMDLSConnectionParameters()
    info.organizationID = "Put your organizationID here."
    mCameraEnhancer!!.initLicenseFromDLS(info) { isSuccess, error ->
        if (!isSuccess) {
            error.printStackTrace()
        }
    }
```

For iOS users:

Objective-C sample

```objectivec
    iDCEDLSConnectionParameters* dcePara = [[iDCEDLSConnectionParameters alloc] init];
    dcePara.organizationID = @"Your organizationID";
    dce = [[DynamsoftCameraEnhancer alloc] initLicenseFromDLS:dcePara view:dceview verificationDelegate:self];
```

Swift sample

```swift
    let DLS = iDCEDLSConnectionParameters()
    DLS.organizationID = "Your organizationID"
    dce = DynamsoftCameraEnhancer.init(licenseFromDLS: DLS, view: dceView, verificationDelegate: self)
```
