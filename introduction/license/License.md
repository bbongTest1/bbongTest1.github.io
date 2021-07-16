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

## Set up the license from License Tracking Server

Once you have a license you can use following code to set up your license from `LTS`:

For Android users:

Android sample

Java:

```java
    DMLTSConnectionParameters info = new DMLTSConnectionParameters();
    info.organizationID = "Your organizationID";
    mCamera.initLicenseFromLTS(info, new CameraLTSLicenseVerificationListener() {
        @Override
        public void LTSLicenseVerificationCallback(boolean b, Exception e) {
            if(!b && e != null){
                e.printStackTrace();
            }
        }
    });
```

Kotlin:

```kotlin
    val info = com.dynamsoft.dce.DMLTSConnectionParameters()
    info.organizationID = "Put your organizationID here."
    mCameraEnhancer!!.initLicenseFromLTS(info) { isSuccess, error ->
        if (!isSuccess) {
            error.printStackTrace()
        }
    }
```

For iOS users:

Objective-C sample

```objectivec
    iDCELTSConnectionParameters* dcePara = [[iDCELTSConnectionParameters alloc] init];
    dcePara.organizationID = @"Your organizationID";
    dce = [[DynamsoftCameraEnhancer alloc] initLicenseFromLTS:dcePara view:dceview verificationDelegate:self];
```

Swift sample

```swift
    let lts = iDCELTSConnectionParameters()
    lts.organizationID = "Your organizationID"
    dce = DynamsoftCameraEnhancer.init(licenseFromLTS: lts, view: dceView, verificationDelegate: self)
```
