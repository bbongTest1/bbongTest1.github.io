---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android DMDLSConnectionParameters Class
description: This is the documentation - Android DMDLSConnectionParameters Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android DMDLSConnectionParameters Class
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: Android DMDLSConnectionParameters Class
---

# com.dynamsoft.dce.DMDLSConnectionParameters

`DMDLSConnectionParameters` is the class that defines a struct to configure the parameters to connect to the Dynamsoft License Server.

Java:

```Java
private com.dynamsoft.dce.DMDLSConnectionParameters dceParameters;
dceParameters = new com.dynamsoft.dce.DMDLSConnectionParameters();
```

Kotlin:

```kotlin
private var dceParameters: com.dynamsoft.dce.DMDLSConnectionParameters? = null
dceParameters = com.dynamsoft.dce.DMDLSConnectionParameters()
```

| Attribute Name | Type |
|------|------|
| [`mainServerURL`](#mainserverurl) | String |
| [`standbyServerURL`](#standbyserverurl) | String |
| [`handshakeCode`](#handshakecode) | String |
| [`organizationID`](#organizationid) | String |
| [`sessionPassword`](#sessionpassword) | String |
| [`uuidGenerationMethod`](#uuidgenerationmethod) | int |
| [`maxBufferDays`](#maxbufferdays) | int |
| [`limitedLicenseModules`](#limitedlicensemodules) | list |
| [`chargeWay`](#chargeway) | int |
| [`products`](#products) | int |

## mainServerURL

The URL of the Dynamsoft License Server.

Java:

```java
dceParameters.mainServerURL = "";
```

Kotlin:

```kotlin
dceParameters!!.mainServerURL = ""
```

- **Value range**
    Any string value

- **Default value**
    null

- **Remarks**
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft License Servers for online verification.

## standbyServerURL

The URL of the standby Dynamsoft License Server.

Java:

```java
dceParameters.standbyServerURL = "";
```

Kotlin:

```kotlin
dceParameters!!.standbyServerURL = ""
```

- **Value range**
    Any string value

- **Default value**
    null

- **Remarks**
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft License Servers for online verification.

## handshakeCode

The handshake code.

Java:

```java
dceParameters.handshakeCode = "";
```

Kotlin:

```kotlin
dceParameters!!.handshakeCode = ""
```

- **Value range**
    Any string value

- **Default value**
    null

## organizationID

The organization ID

Java:

```java
dceParameters.organizationID = "";
```

Kotlin:

```kotlin
dceParameters!!.organizationID = ""
```

- **Value range**
    Any string value

- **Default value**
    null

## sessionPassword

The session password of the handshake code set in Dynamsoft License Server.

Java:

```java
dceParameters.sessionPassword = "";
```

Kotlin:

```kotlin
dceParameters!!.sessionPassword = ""
```

- **Value range**
    Any string value

- **Default value**
    null

## uuidGenerationMethod

Sets the method to generate UUID.

Java:

```java
dceParameters.uuidGenerationMethod = int;
```

Kotlin:

```kotlin
dceParameters!!.uuidGenerationMethod = int
```

- **Value range**
    Any one of the [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}dmuuidgeneration.html) Enumeration items.

- **Default value**
    DM_UUIDGM_RANDOM

- **See also**  
    [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}dmuuidgeneration.html)

## maxBufferDays

Sets the max days to buffer the license info.

Java:

```java
dceParameters.maxBufferDays = int;
```

Kotlin:

```kotlin
dceParameters!!.maxBufferDays = int
```

- **Value range**
    [7,0x7fffffff]  

- **Default value**
    7

## chargeWay

Sets the charge way.

Java:

```java
dceParameters.chargeWay = int;
```

Kotlin:

```kotlin
dceParameters!!.chargeWay = int
```

- **Value range**
    Any one of the [`EnumDMChargeWay`]({{ site.enumerations }}dmchargeway.html) Enumeration items.

- **Default value**
    DM_CW_AUTO

- **See also**  
    [`EnumDMChargeWay`]({{ site.enumerations }}dmchargeway.html)

## products

Set the products. This is a combined value of Product Enumration items.

Java:

```java
dceParameters.products = int;
```

Kotlin:

```kotlin
dceParameters!!.products = int
```

- **Value range**
    Any one of the [`EnumProduct`]({{ site.enumerations }}enumproduct.html) Enumeration items.

- **See also**  
    [`EnumProduct`]({{ site.enumerations }}enumproduct.html)
