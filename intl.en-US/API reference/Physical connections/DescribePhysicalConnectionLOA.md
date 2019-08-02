# DescribePhysicalConnectionLOA {#doc_api_Vpc_DescribePhysicalConnectionLOA .reference}

Queries LOA information about a physical connection.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=DescribePhysicalConnectionLOA) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribePhysicalConnectionLOA| The name of this action.

 Value: **DescribePhysicalConnectionLOA**

 |
|InstanceId|String|Yes|pc-bp1ca4wca27exxxxxxxx| The instance ID of the physical connection.

 |
|RegionId|String|Yes|cn-hangzhou| The region of the physical connection.

 |
|ClientToken|String|No|318BB676-0A2B-43A0-9AD8-F1D34E93750F| Optional. The client token used for authentication.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|PhysicalConnectionLOAType| | | The LOA information of the physical connection.

 |
|CompanyLocalizedName|String|company| The company name that you set when you registered your account.

 |
|CompanyName|String|test1234| The name of the company that requires the leased line.

 |
|ConstructionTime|String|2019-02-26T08:00:00Z| The time when the data center cable installation technician or representative will go to the installation site.

 |
|InstanceId|String|pc-bp1ca4wca27exxxxxxxxx| The instance ID of the physical connection.

 |
|LineCode|String|aaa111| The code of the leased line.

 |
|LineLabel|String|bbb222| The label numbers of the cables at the installation site.

 |
|LineType|String|MSTP| The type of the physical connection.

 Valid values:

 -   MSTP
-   Other
-   SDH
-   MPLSVPN
-   FIBRE

 |
|LoaUrl|String|http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928\_pc-bp1ca4wca27ertsucaxn0\_cn-hangzhou-dg-a01.pdf?Expires=1551164196&OSSAccessKeyId=dCrRKgLiFLLHAo6k&Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D| The URL used to download the LOA file.

 |
|PMInfo| | | The information about the data center cable installation technician or representative.

 |
|PMCertificateNo|String|12345671223| The certificate or licence number of the data center cable installation technician or representative.

 |
|PMCertificateType|String|Other| The type of certificate or licence held by the data center cable installation technician or representative.

 |
|PMContactInfo|String|18910010000| The contact information of the data center cable installation technician or representative.

 |
|PMGender|String|Male| The gender of the data center cable installation technician or representative.

 |
|PMName|String|name| The name of the data center cable installation technician or representative.

 |
|SI|String|ctcu| The name of the data center cable installation company.

 |
|Status|String|Available | The status of the physical connection.

 |
|RequestId|String|318BB676-0A2B-43A0-9AD8-F1D34E93750F| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribePhysicalConnectionLOA
&InstanceId=pc-bp1ca4wca27exxxxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribePhysicalConnectionLOAResponse>
  <code>200</code>
  <data>
    <companyName>test1234</companyName>
    <constructionTime>2019-02-26T08:00:00Z</constructionTime>
    <instanceId>pc-bp1ca4wca27ertsucaxn0</instanceId>
    <LineType> MSTP </lineType>
    <loaUrl>http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928_pc-bp1ca4wca27ertsucaxn0_cn-hangzhou-dg-a01.pdf?Expires=1551164196&amp;OSSAccessKeyId=dCrRKgLiFLLHAo6k&amp;Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D</loaUrl>
    <pmInfo>
      <nextPMIndex>1</nextPMIndex>
      <PmCertificateNo> 1234567 </pmCertificateNo>
      <pmCertificateType>Other</pmCertificateType>
      <pmContactInfo>18910010000</pmContactInfo>
      <pmGender>Male</pmGender>
      <pmName>test</pmName>
    </pmInfo>
    <si>ctcu</si>
    <status>Available</status>
  </data>
  <message>successful</message>
  <requestId>318BB676-0A2B-43A0-9AD8-F1D34E93750F</requestId>
  <success>true</success>
</DescribePhysicalConnectionLOAResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"message":"successful",
	"requestId":"318BB676-0A2B-43A0-9AD8-F1D34E93750F",
	"data":{
		"lineType":"MSTP",
		"status":"Available",
		"pmInfo":[
			{
				"pmContactInfo":"18910010000",
				"pmGender":"Male",
				"pmCertificateNo":"1234567",
				"PmCertificateType": "Other ",
				"nextPMIndex":1,
				"pmName":"test"
			}
		],
		"instanceId":"pc-bp1ca4wca27ertsucaxn0",
		"constructionTime":"2019-02-26T08:00:00Z",
		"companyName":"test1234",
		"si":"ctcu",
		"loaUrl":"http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928_pc-bp1ca4wca27ertsucaxn0_cn-hangzhou-dg-a01.pdf?Expires=1551164196&OSSAccessKeyId=dCrRKgLiFLLHAo6k&Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D"
	},
	"code":"200",
	"success":true
}
```

## Error codes {#section_bg3_6sc_6ot .section}

