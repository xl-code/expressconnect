# ModifyExpressCloudConnectionBandwidth {#doc_api_Vpc_ModifyExpressCloudConnectionBandwidth .reference}

Modifies the bandwidth of an Express Cloud Connect \(ECC\) instance.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=ModifyExpressCloudConnectionBandwidth&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String |Yes|ModifyExpressCloudConnectionBandwidth|The name of this action.

 Value: **ModifyExpressCloudConnectionBandwidth**

 |
|EccId|String |Yes|ecc-xxxxxxxxx|The ID of the ECC instance.

 |
|RegionId|String |Yes|cn-hangzhou|The ID of the region to which the ECC instance belongs.

 |
|Bandwidth|String|No|2|Optional. The bandwidth of the ECC instance.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|E6385514-B0CC-48E3-B9F9-F7BFF64460A2|The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyExpressCloudConnectionBandwidth
&EccId=ecc-xxxxxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyExpressCloudConnectionBandwidthResponse>
	  <RequestId>E6385514-B0CC-48E3-B9F9-F7BFF64460A2</RequestId>
    </ModifyExpressCloudConnectionBandwidthResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"E6385514-B0CC-48E3-B9F9-F7BFF64460A2"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|You are not authorized to operate on this resource. Please apply for the permission and try again later.|
|403|Forbidden|User not authorized to operate on the specified resource.|You are not authorized to operate on this resource. For more details, open a ticket.|

