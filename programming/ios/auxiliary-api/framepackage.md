---
layout: default-layout
title: Dynamsoft Camera Enhancer - iOS FramePackage Class
description: This is the documentation - iOS FramePackage Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, iOS FramePackage Class
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: iOS FramePackage Class
---

# FramePackage

Return the frame decode results and additional information.

| Attribute Name | Type |
|------|------|
| [`buffer`](#buffer) | NSData* |
| [`width`](#width) | NSNumber* |
| [`height`](#height) | NSNumber* |
| [`stride`](#stride) | NSNumber* |
| [`pixelFormat`](#pixelformat) | NSString* |
| [`frameID`](#frameid) | NSNumber* |
| [`fastFrameID`](#fastframeid) | NSNumber* |
| [`imageBuffer`](#imagebuffer) | CVImageBufferRef |

## buffer

Store the buffered frame data in NSData.

```objectivec
NSData* buffer
```

## width

Store the width of the frame.

```objectivec
NSNumber* width
```

## height

Store the height of the frame.

```objectivec
NSNumber* height
```

## stride

Store the stride of the frame.

```objectivec
NSNumber* stride
```

## pixelFormat

Store the pixel format of the frame.

```objectivec
NSString* pixelFormat
```

## frameID

Store the frame ID of the frame.

```objectivec
NSNumber* frameID
```

## fastFrameID

Store the fast frame ID of the frame.

```objectivec
NSNumber* fastFrameID
```

## imageBuffer

Store the buffered frame data in CVImageBufferRef.

```objectivec
CVImageBufferRef imageBuffer
```
