# QueryDeviceByTags {#reference_pgk_qck_sfb .reference}

You can call this operation to query devices by tags.

## Limits {#section_plt_vdm_2gb .section}

Up to ten tags can be used at one time.

## Request parameters {#section_sm5_5ck_sfb .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Set the value to QueryDeviceByTags.|
|PageSize|Integer|No|The number of devices per page in the response. The maximum limit is 50. The default value is 10.|
|CurrentPage|Integer|No|The number of the page to be displayed. The default value is 1.|
|Tag|List<Tag\>|Yes|The device tags. Quantity limit: up to 10 tags can be entered.Tag includes TagKey and TagValue, which correspond to the key and value of a tag respectively.

You can specify a TagKey without a TagValue.

For more information about tags, see the following table Tag.

|
|Common request parameters|-|Yes|For more information about common request parameters, see [Common parameters](reseller.en-US/Developer Guide (Cloud)/API reference/Common parameters.md#).|

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|TagKey|String|Yes|The key of the device tag.|
|TagValue| String| No|The value of the device tag.|

## Response parameters {#section_urg_42k_sfb .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|RequestId|String|The globally unique ID generated by Alibaba Cloud for the request.|
|Success|Boolean|Indicates whether the call is successful. A value of true indicates that the call is successful. A value of false indicates that the call has failed.|
|ErrorMessage|String|The error message returned when the call fails.|
|Code|String|The error code returned when the call fails. For more information about error codes, see [Error codes](reseller.en-US/Developer Guide (Cloud)/API reference/Error codes.md#).|
|PageCount|Integer|The total number of pages.|
|PageSize|Integer  |The number of devices displayed per page.|
|Page|Integer|The current page number.|
|Total|Integer|The total number of devices.|
|Data|Data|The list of device information returned when the call is successful. For more information, see the following SimpleDeviceInfo table.|

|Parameter|Type|Description|
|:--------|:---|:----------|
|ProductName|String|The name of the product which the device belongs to.|
|ProductKey|String|The unique identifier of the product which the device belongs to.|
|DeviceName|String|The device name.|
|IotId|String|The globally unique ID issued by IoT Platform to the device.|

## Examples {#section_qbk_fgk_sfb .section}

**Request example**

```
https://iot.cn-shanghai.aliyuncs.com/?Action=QueryDeviceByTags
&CurrentPage=1
&PageSize=10
&Tag. 1. TagKey=dfdfd
&Tag. 1. TagValue=dfdfdfdf
&Tag. 2. TagKey=ddfdfdf
&Tag. 2. TagValue=dfdfdfdfd
&Common request parameters
```

**Response example**

-   JSON format

    ```
    {
        "PageCount": 1,
        "Data": {
            "SimpleDeviceInfo": [
                {
                    "DeviceName": "1102jichu02",
                    "ProductKey": "a1SM5S1shy1",
                    "IotId": "GookTiUcwqRbHosp9Ta10017d3a00",
                    "ProductName": "TEST"
                }
            ]
        },
        "PageSize": 10,
        "Page": 1,
        "RequestId": "2B5091E4-32D5-4884-A5B2-2E8E713D84AF",
        "Success": true,
        "Total": 1
    }
    ```

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <QueryDeviceByTags>
    	<PageCount>1</PageCount>
    	<Data>
    		<SimpleDeviceInfo>
    			<DeviceName>1102jichu02</DeviceName>
    			<ProductKey>a1SM5S1shy1</ProductKey>
    			<IotId>GookTiUcwqRbHosp9Ta10017d3a00</IotId>
    			<ProductName>TEST</ProductName>
    		</SimpleDeviceInfo>
    	</Data>
    	<PageSize>10</PageSize>
    	<Page>1</Page>
    	<RequestId>2B5091E4-32D5-4884-A5B2-2E8E713D84AF</RequestId>
    	<Success>true</Success>
    	<Total>1</Total>
    </QueryDeviceByTags>
    ```


