# ApplyPhysicalConnectionLOA {#doc_api_1031799 .reference}

Apply for the LOA.

## Debug {#apiExplorer .section}

Perform a [debug](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) in OpenAPI Explorer. We recommend that you use OpenAPI Explorer. By using OpenAPI Explorer, you can call APIs, generate SDK code examples automatically, and search APIs, allowing you to quickly and easily get started with using APIs on the cloud.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ApplyPhysicalConnectionLOA| The action to perform.

 Valid value: **ApplyPhysicalConnectionLOA**.

 |
|CompanyName|String|Yes|company| The name of the company that requires the physical connection.

 |
|ConstructionTime|String|Yes|2019-02-28T16:00:00.000Z| The date and time when the data cable installation technician or representative will go to the installation site.

 |
|InstanceId|String|Yes|pc-bp1qrb3044eqixxxxxxxx| The instance ID of the physical connection interface.

 |
|LineType|String|Yes|SDH| The type of leased line.

 |
|PeerLocation|String|Yes|Hangzhou| The location where the leased line is deployed.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the physical connection interface belongs.

 |
|Si|String|Yes|Alibaba Cloud| The name of the installation company.

 |
|Bandwidth|Integer|No|3| Optional. The bandwidth value of the physical connection.

 |
|ClientToken|String|No|A47BD386-7FDE-4xxx4-8D22-C62xxxxxxxx| Optional. The token used for client authentication.

 |
|LineOperator|String|No|CU| Optional. The service provider that provides the leased line.

 |
|PMInfo.N.PMCertificateNo|String|No|3210xxxxxxxxxxxxxx| Optional. The license number of the certificate held by the data cable installation technician or representative.

 |
|PMInfo.N.PMCertificateType|String|No|IDCard| Optional. The type of the certificate that the data cable installation technician or representative holds.

 |
|PMInfo.N.PMContactInfo|String|No|13200000000| Optional. The contact information of the data cable installation technician or representative.

 |
|PMInfo.N.PMGender|String|No|Male| Optional. The gender of the data cable installation technician or representative.

 |
|PMInfo.N.PMName|String|No|Mike| Optional. The name of the data cable installation technician or representative.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|A47BD386-7FDE-42C4-8D22-C6223D18AA1C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/?CompanyName=company
&ConstructionTime=2019-02-28T16:00:00.000Z
&InstanceId=pc-bp1qrb3044eqixxxxxxxx
&LineType=SDH
&PeerLocation=Hangzhou
&RegionId=cn-hangzhou
&Si=Alibaba Cloud
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<ApplyPhysicalConnectionLOA>
  <code>200</code>
  <httpStatusCode>200</httpStatusCode>
  <message>successful</message>
  <requestId>A47BD386-7FDE-42C4-8D22-C6223D18AA1C</requestId>
  <success>true</success>
</ApplyPhysicalConnectionLOA>

```

`JSON` format

``` {#json_return_success_demo}
{
	"message":"successful",
	"httpStatusCode":200,
	"requestId":"A47BD386-7FDE-42C4-8D22-C6223D18AA1C",
	"code":"200",
	"success":true
}
```

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Vpc)

