---
layout: default-layout
title: Dynamsoft Camera Enhancer - iOS iDCEDLSConnectionParameters Class
description: This is the documentation - iOS iDCEDLSConnectionParameters Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, iOS iDCEDLSConnectionParameters Class
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: iOS iDCEDLSConnectionParameters Class
---

# iDCEDLSConnectionParameters

Defines a struct to configure the parameters to connect to the Dynamsoft License Server.

| Attribute Name | Type |
|------|------|
| [`mainServerURL`](#mainserverurl) | NSString* |
| [`standbyServerURL`](#standbyserverurl) | NSString* |
| [`organizationID`](#organizationid) | NSString* |
| [`handshakeCode`](#handshakecode) | NSString* |
| [`sessionPassword`](#sessionpassword) | NSString* |
| [`chargeWay`](#chargeway) | EnumDMChargWay |
| [`UUIDGenerationMethod`](#uuidgenerationmethod) | EnumDMUUIDGenerationMethod |
| [`maxBufferDays`](#maxbufferdays) | NSInteger |
| [`limitedLicenseModules`](#limitedlicensemodules) | NSArray* |
| [`products`](#products) | NSInteger |

## mainServerURL

The URL of the Dynamsoft License Server.

```objectivec
NSString* mainServerURL
```

## standbyServerURL

The URL of the standby Dynamsoft License Server.

```objectivec
NSString* standbyServerURL
```

## organizationID

Set the organization ID.

```objectivec
NSString* organizationID
```

## handshakeCode

The handshake code.

```objectivec
NSString* handshakeCode
```

## sessionPassword

The session password of the handshake code set in Dynamsoft License Server.

```objectivec
NSString* sessionPassword
```

## chargeWay

Set the charge way.

```objectivec
EnumDMChargeWay chargeWay
```

## UUIDGenerationMethod

Set the method to generate UUID.

```objectivec
EnumDMUUIDGenerationMethod UUIDGenerationMethod
```

## maxBufferDays

Set the max days to buffer the license info.

```objectivec
NSInteger maxBufferDays
```

## limitedLicenseModules

Set the count of license modules to use.

```objectivec
NSArray* limitedLicenseModules
```

## products

Set the products. This is a combined value of Product Enumration items.

```objectivec
NSInteger products
```
