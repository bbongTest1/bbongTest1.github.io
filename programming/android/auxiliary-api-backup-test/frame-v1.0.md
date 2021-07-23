---
layout: default-layout
title: Dynamsoft Camera Enhancer - Android Frame Class
description: This is the documentation - Android Frame Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Android, Frame
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: Android Frame Class
---

# com.dynamsoft.dce.Frame

This page is for `Frame` Class. `Frame` parameters store the frame data.

| Method Name | Type |
|------|------|
| [`getData`](#getdata) | byte[] |
| [`getWidth`](#getwidth) | int |
| [`getHeight`](#getheight) | int |
| [`getStrides`](#getstrides) | int[] |
| [`getFormat`](#getformat) | int |
| [`getFrameId`](#getframeid) | int |
| [`isFastFrame`](#isfastframe) | boolean |
| [`getFastFrameId`](#getfastframeid) | int |
| [`getCropRect`](#getcroprect) | Rect |
| [`getOrientation`](#getorientation) | int |
| [`getOriW`](#getoriw) | int |
| [`getOriH`](#getorih) | int |

## getData

Get the frame data in byte array.

Java:

```java
Frame frame;
byte[] data = frame.getData();
```

Kotlin:

```kotlin
var frame: Frame? = null
var data: ByteArray? = frame!!.data
```

## getWidth

Get the frame width in pixels.

Java:

```java
int width = frame.getWidth();
```

Kotlin:

```kotlin
var width: Int? = frame!!.width
```

## getHeight

Get the frame height in pixels.

Java:

```java
int height = frame.getHeight(); 
```

Kotlin:

```kotlin
var height: Int? = frame!!.height
```

## getStrides

Get the frame strides.

Java:

```java
int[] strides = frame.getStrides();
```

Kotlin:

```kotlin
var strides: IntArray? = frame!!.strides
```

## getFormat

Get the frame pixel format.

Java:

```java
int format = frame.getFormat();
```

Kotlin:

```kotlin
var format: Int? = frame!!.format
```

## getFrameId

Get the frame ID.

```java
int frameid = frame.getFrameId(); 
```

Kotlin:

```kotlin
var frameid: Int? = frame!!.frameId
```

## isFastFrame

Check whether the fast mode is enabled.

Java:

```java
boolean isfastframe = frame.isFastFrame();
```

Kotlin:

```kotlin
var isfastframe: Boolean? = frame!!.isFastFrame
```

## getFastFrameId

Get the fast frame (cropped frame) ID.

Java:

```java
int fastframeid = frame.getFastFrameId();
```

Kotlin:

```kotlin
var fastframeid: Int? = frame!!.fastFrameId
```

## getCropRect

Get the cropped Rect data (Width & height)

Java:

```java
Rect croprect = frame.getCropRect();
```

Kotlin:

```kotlin
var croprect: Rect? = frame!!.cropRect
```

## getOrientation

Get the orientation (of cropped frame).

| Orientation of the frame | Value |
|--------------------------|-------|
| Vertical | 1 |
| Horizontal | 2 |

Java:

```java
int orientation = frame.getOrientation();
```

Kotlin:

```kotlin
var orientation: Int? = frame!!.getOrientation
```

## getOriW

Get the original width of the cropped frame.

Java:

```java
int originalwidth = frame.getOriW();
```

Kotlin:

```kotlin
var originalwidth: Int? = frame!!.getOriW
```

## getOriH

Get the original width of the cropped frame.

Java:

```java
int originalheight = frame.getOriH();
```

Kotlin:

```kotlin
var originalheight: Int? = frame!!.getOriH
```
