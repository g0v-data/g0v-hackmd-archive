# EFI Driver Dev Guide
EFI 1.10 version

### About EFI :bulb: 

#### Objects managed by EFI-based firmware

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a8594f7763e2b24c8456f677d92787a0.png)

#### EFI System Table
The data structure which can access configuration and service like boot, runtime, protocol...

#### Handle database :pushpin: 
* Handle database = a group of handles
* Handle = a group of protocols

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_51ebca8d2e88f22ba6dfaf1d5b70e12d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_330c08975b88e28a6e4bcc605a17e33e.png)

在ExitBootServices()被呼叫後，Handle Database將不復存在

#### Protocols 
* Protocol = a group of functions + private data, which are named by Globally Unique Identifier(GUID)
* Protocol provides software abstraction for device like console, disk, network...

```C=
#define EFI_COMPONENT_NAME_PROTOCOL_GUID {0x.....}

typedef struct _EFI_COMPONENT_NAME_PROTOCOL{
    EFI_COMPONENT_NAME_GET_DRIVER_NAME GetDriverName;
    EFI_COMPONENT_NAME_GET_CONTROLLER_NAME GetControllerName;
    CHAR8 *SupportedLanguages;
} EFI_COMPONENT_NAME_PROTOCOL;

```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b8592d7516ef6a1d832f9cadfb3877c4.png)

#### EFI images
>EFI applications
>EFI Boot Service drivers
>EFI Runtime drivers

Image can be loaded from storage locations like ROM, flash, hard disk, floppy, CD-ROM, DVD, or LAN boot server...

協議: EFI_LOADED_IMAGE_PROTOCOL
加載: gBS->LoadImage()
開啟: gBS->StartImage()

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6fa73d962c2c98e254aef21d24b92cc4.png)


#### Events
>Set Event
>Exit Event
>Check Event
>Wait for Event

EFI support polling, instead of interrupt

Task Priority Level(TPL)
|Task Priority Level|Description|
|---|---|
|TPL_APPLICATION|The priority level at which EFI images are executed.|
|TPL_CALLBACK|The priority level for most notification functions.|
|TPL_NOTIFY|The priority level at which most I/O operations are performed.|
|TPL_HIGH_LEVEL|The priority level for the one timer interrupt supported in EFI.|


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac390ea3a8636682c2c4e681f7f286f3.png)


#### Device paths

#### EFI Driver Model

#### Platform initialization

#### Boot manager and console management



## EFI Coding :bulb: 

## EFI Serveice :bulb: 

## Driver Design :bulb: 

## Driver Entry Point :bulb: 

## Driver Binding Protocol :bulb: 

## Build & Test Driver :bulb: 

