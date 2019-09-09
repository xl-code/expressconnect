# ModifyExpressCloudConnectionAttribute {#doc_api_Vpc_ModifyExpressCloudConnectionAttribute .reference}

Modifies the attribute of an Express Cloud Connect \(ECC\) instance.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=ModifyExpressCloudConnectionAttribute&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String |Yes|ModifyExpressCloudConnectionAttribute|The name of this action.

 Value: **ModifyExpressCloudConnectionAttribute**

 |
|EccId|String |Yes|ecc-bp1t9osmuln\*\*\*\*\*\*\*|The ID of the ECC instance.

 |
|RegionId|String |Yes|cn-hangzhou|The ID of the region to which the ECC instance belongs.

 |
|Description|String |No|ECC|Optional. The description of the ECC instance.

 |
|Name|String|No|doctest|Optional. The name of the ECC instance.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|E6385514-B0CC-48E3-B9F9-F7BFF64460A2|The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyExpressCloudConnectionAttribute
&EccId=ecc-bp1t9osmuln*******
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyExpressCloudConnectionAttributeResponse>
	  <RequestId>E6385514-B0CC-48E3-B9F9-F7BFF64460A2</RequestId>
    </ModifyExpressCloudConnectionAttributeResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"E6385514-B0CC-48E3-B9F9-F7BFF64460A2"
}
```

## Errors { .section}

