# Firmware update {#concept_swx_ttw_y2b .concept}

For information about the firmware update, see [Develop OTA features](../../../../../reseller.en-US//Develop OTA features.md#) and [Firmware update](../../../../../reseller.en-US/User Guide/Monitoring and Maintenance/Firmware update.md#).

## Report the firmware version {#section_ivm_fbh_12b .section}

Upstream​

-   Topic: /ota/device/inform/\{productKey\}/\{deviceName\}

    The device publishes a message to this topic to report the current firmware version to IoT Platform.


Request message

```
{
  "id": 1,
  "params": {
    "version": "1.0.1"
  }
}
```

​Parameter description​

|Parameter|Type|Description|
|:--------|:---|:----------|
|id|String|Message ID.|
|version|String |Version information of the firmware.|

## Push firmware information​ {#section_jjq_4bx_y2b .section}

Downstream

-   Topic: /ota/device/upgrade/\{productKey\}/\{deviceName\}

    IoT Platform publishes messages to this topic to push firmware information. The devices subscribe to this topic to obtain the firmware information.


Request message

```
{
  "code": "1000",
  "data": {
    "size": 432945,
    "version": "2.0.0",
    "url": "https://iotx-ota-pre.oss-cn-shanghai.aliyuncs.com/nopoll_0.4.4.tar.gz?Expires=1502955804&OSSAccessKeyId=XXXXXXXXXXXXXXXXXXXX&Signature=XfgJu7P6DWWejstKJgXJEH0qAKU%3D&security-token=CAISuQJ1q6Ft5B2yfSjIpK6MGsyN1Jx5jo6mVnfBglIPTvlvt5D50Tz2IHtIf3NpAusdsv03nWxT7v4flqFyTINVAEvYZJOPKGrGR0DzDbDasumZsJbo4f%2FMQBqEaXPS2MvVfJ%2BzLrf0ceusbFbpjzJ6xaCAGxypQ12iN%2B%2Fr6%2F5gdc9FcQSkL0B8ZrFsKxBltdUROFbIKP%2BpKWSKuGfLC1dysQcO1wEP4K%2BkkMqH8Uic3h%2Boy%2BgJt8H2PpHhd9NhXuV2WMzn2%2FdtJOiTknxR7ARasaBqhelc4zqA%2FPPlWgAKvkXba7aIoo01fV4jN5JXQfAU8KLO8tRjofHWmojNzBJAAPpYSSy3Rvr7m5efQrrybY1lLO6iZy%2BVio2VSZDxshI5Z3McKARWct06MWV9ABA2TTXXOi40BOxuq%2B3JGoABXC54TOlo7%2F1wTLTsCUqzzeIiXVOK8CfNOkfTucMGHkeYeCdFkm%2FkADhXAnrnGf5a4FbmKMQph2cKsr8y8UfWLC6IzvJsClXTnbJBMeuWIqo5zIynS1pm7gf%2F9N3hVc6%2BEeIk0xfl2tycsUpbL2FoaGk6BAF8hWSWYUXsv59d5Uk%3D",
    "md5": "93230c3bde425a9d7984a594ac55ea1e",
    "sign": "93230c3bde425a9d7984a594ac55ea1e",
    "signMethod": "Md5"
  },
  "id": 1507707025,
  "message": "success"
}
```

​Parameter description​

|Parameter|Type|Description|
|:--------|:---|:----------|
|id|String|Message ID.|
|message|String|Result information.​|
|version|String|Version information of the firmware.|
|size|Long|Firmware size in bytes.|
|url|String |OSS address of the firmware.|
|sign|String|​Firmware signature.​|
|signMethod|String|Signing method. Currently, the supported methods are MD5 and sha256.|
|md5|String |This parameter is reserved. This parameter is used to be compatible with old device information. When the signing method is MD5, IoT Platform will assign values to both the sign and md5 parameters.|

## Report update progress {#section_nrg_pbx_y2b .section}

Upstream

-   Topic: /ota/device/progress/\{productKey\}/\{deviceName\}

    A device subscribes to this topic to report the firmware update progress.


Request message

```
{
  "id": 1,
  "params": {
    "step": "-1",
    "desc": "Firmware update has failed. No firmware information is available."
  }
}
```

​Parameter description​

|Parameter|Type|Description|
|:--------|:---|:----------|
|id|String|Message ID.|
|step|String | Firmware update progress information.

 Value range:

-   A value from 1 to 100 indicates the progress percentage.
-   A value of -1 indicates the firmware update has failed.
-   A value of -2 indicates that the firmware download has failed.
-   A value of -3 indicates that firmware verification has failed.
-   A value of -4 indicates that the firmware installation has failed.

 |
|desc|String |Description of the current step. If an exception occurs, this parameter displays an error message.|

## Request firmware information from IoT Platform {#section_bk5_pbx_y2b .section}

-   Topic: /ota/device/request/\{productKey\}/\{deviceName\}

Request message

```
{
  "id": 1,
  "params": {
    "version": "1.0.1"
  }
}
```

​Parameter description​

|Parameter|Type|Description|
|:--------|:---|:----------|
|id|String|Message ID.|
|version|String|Version information of the firmware.|

