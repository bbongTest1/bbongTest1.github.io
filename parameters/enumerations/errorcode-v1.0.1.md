---
layout: default-layout
title: Dynamsoft Camera Enhancer - Enumerations Error code
description: This is the documentation - Enumerations Error code page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, Enumerations Error code
needAutoGenerateSidebar: true
breadcrumbText: Enumerations Error code
---

# Enumerations Error code

## Declarations

| Language | Declaration |
|----------|-------------|
| Java(Android) | `class EnumDCEErrorCode` |
| Objective-C & Swift | `enum EnumDCEErrorCode` |

## Members

| Error Code (Android) | Error Code (iOS) | Value | Description |
|----------------------|------------------|-------|-------------|
| `DCE_OK` | `EnumCameraErrorCode_OK`  | 0 | Successful. |
| `DCE_LICENSE_INVALID` | `EnumCameraErrorCode_LICENSE_INVALID` | -10001 | The licence is invalid. |
| `DCE_LICENSE_EXPIRED` | `EnumCameraErrorCode_LICENSE_EXPIRED` | -10002 | The licence has expired. |
| `DCE_NOT_EXIST_CAMERA_MODULE` | `EnumCameraErrorCode_NOT_EXIST_CAMERA_MODULE` | -10003 | Camera module does not exist. |
| `DCE_NOT_FOUND_FILE` | `EnumCameraErrorCode_NOT_FOUND_FILE` | -10004 | File is not found. |
| `DCE_FILE_FORMAT_ERROR` | `EnumCameraErrorCode_FILE_FORMAT_ERROR` | -10005 | File format error. |
| `DCE_LICENSEKEY_NOT_MATCHED` | Not available for iOS. | -10043 | The license key does not match the license content. |
| Not available for Android | `EnumCameraErrorCode_Requested_Failed` | -10044 | The license key does not match the license content. |
| `DM_NO_LICENSE` | `EnumCameraErrorCode_NO_LICENSE` | -20000 | There is no license specified. |
| `DM_HANDSHAKE_CODE_INVALID` | `EnumCameraErrorCode_HANDSHAKE_CODE_INVALID` | -20001 | Handshake code is invalid. |
| `DM_LICENSE_BUFFER_FAILED` | `EnumCameraErrorCode_LICENSE_BUFFER_FAILED` | -20002 | Failed to read or write license buffer. |
| `DM_LICENSE_SYNC_FAILED` | `EnumCameraErrorCode_LICENSE_SYNC_FAILED` | -20003 | Failed to synchronize license info with license tracking server. |
| `DM_DEVICE_NOT_MATCH` | `EnumCameraErrorCode_DEVICE_NOT_MATCH` | -20004 | Device does not match with license buffer. |
| `DM_BIND_DEVICE_FAILED` | `EnumCameraErrorCode_BIND_DEVICE_FAILED` | -20005 | Failed to bind device. |
| `DM_LICENSE_INTERFACE_CONFLICT` | `EnumCameraErrorCode_LICENSE_INTERFACE_CONFLICT` | -20006 | Interface InitLicenseFromLTS can not be used together with other license initiation interfaces. |
| `DM_LICENSE_CLIENT_DLL_MISSING` | `EnumCameraErrorCode_LICENSE_CLIENT_DLL_MISSING` | -20007 | The license client dll is missing. |
| `DM_INSTANCE_COUNT_OVER_LIMITED` | `EnumCameraErrorCode_INSTANCE_COUNT_OVER_LIMITED` | -20008 | The number of instances used has exceeded the limit. |
| `DM_LICENSE_INIT_SEQUENCE_FAILED` | `EnumCameraErrorCode_LICENSE_INIT_SEQUENCE_FAILED` | -20009 | Interface InitLicenseFromLTS has to be called before creating any SDK objects. |
| `DM_TRIAL_LICENSE` | `EnumCameraErrorCode_TRIAL_LICENSE` | -20010 | Using a trial license. |
| `DM_FAILED_TO_REACH_LTS` | `EnumCameraErrorCode_FAILED_TO_REACH_LTS` | -20200 | Fail to connect to license tracking server. |
