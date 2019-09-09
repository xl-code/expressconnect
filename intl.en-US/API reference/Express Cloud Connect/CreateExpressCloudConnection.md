# CreateExpressCloudConnection {#doc_api_Vpc_CreateExpressCloudConnection .reference}

Applies for the Express Cloud Connect \(ECC\) service.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=CreateExpressCloudConnection&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String |Yes|CreateExpressCloudConnection|The name of this action.

 Value: **CreateExpressCloudConnection**

 |
|Bandwidth|Integer|Yes|2|The bandwidth of the ECC instance. Unit: Mbit/s.

 Valid values: **2 | 4 | 6 | 8 | 10 | 20 | 50 | 100 | 200 | 500 | 1000 | 10000 | 40000**

 |
|IdcSP|String|Yes|CU|The service provider of the on-premises data center.

 |
|PeerLocation|String |Yes|5/F, Building XX, XX District|The location of the on-premises data center.

 Enter a detailed location that includes which floor the on-premises data center is.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the ECC instance belongs.

 |
|ContactMail|String|No|XX@example.com|Optional. The email of the person that applies for the ECC service.

 |
|ContactTel|String |No|152XXXXXXXX|Optional. The telephone number of the person that applies for the ECC service.

 |
|Description|String|No|ECC|Optional. The description of the ECC instance.

 The description must be 2 to 256 characters in length and must start with an English letter or a Chinese character. It cannot start with `http://` or `https://`.

 |
|IDCardNo|String|No|32\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|Optional. The ID card number of the person that applies for the ECC service.

 |
|Name|String|No|doctest|Optional. The name of the ECC instance.

 The name must be 2 and 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character. It cannot start with `http://` or `https://`.

 |
|PeerCity|String|No|Hangzhou|Optional. The city where the on-premises data center is located.

 |
|PortType|String|No|100Base-T|Optional. The port type of the physical connection. Valid values:

 -   100Base-T: 100M electrical ports
-   1000Base-T \(default\): 1 Gigabit electrical ports
-   1000Base-LX: 1 Gigabit single-mode optical ports \(10 km\)
-   10GBase-T: 10G electrical ports
-   10GBase-LR: 10G single-mode optical ports \(10 km\)

 |
|RedundantEccId|String|No|ecc-d\*\*\*\*|Optional. The ID of the redundant ECC instance.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|EccId|String |ecc-xxx\*\*\*\*\*|The ID of the created ECC instance.

 |
|RequestId|String|C004F022-1CC2-4958-9937-675513A2CD7E|The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateExpressCloudConnection
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateExpressCloudConnectionResponse>
    <EccId>ecc-bp1t9osmuln1vxfpt6gy8</EccId>
    <RequestId>C004F022-1CC2-4958-9937-675513A2CD7E</RequestId>
</CreateExpressCloudConnectionResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"EccId":"ecc-bp1t9osmuln1vxfpt6gy8",
	"RequestId":"C004F022-1CC2-4958-9937-675513A2CD7E"
}
```

## Errors { .section}

