# DescribeExpressCloudConnections {#doc_api_Vpc_DescribeExpressCloudConnections .reference}

Queries the Express Cloud Connect \(ECC\) instances in a specified region.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeExpressCloudConnections&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeExpressCloudConnections| The name of this action.

 Value: **DescribeExpressCloudConnections**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the ECC instance belongs.

 |
|Filter.N.Key|String|No|2| Optional. The filter condition.

 Value range of N: 1 to 5. The following filter conditions are supported:

 -   eccid: the ECC instance ID
-   bandwidth: the bandwidth of the ECC instance
-   Status: the status of the ECC instance
-   Name: the name of the ECC instance

 The relationship of multiple filter condition values is OR, which means that an ECC instance is returned when it meets any of the specified values. The relationship of multiple filter conditions is AND, which means an ECC instance is returned in the query result only when it meets all the specified filter conditions.

 |
|Filter.N.Value.N|RepeatList|No|3| Optional. The value of the corresponding filter condition. Value range of N: 1 to 5

 |
|PageNumber|Integer|No|1| Optional. The page number of the returned ECC instance list. Default value: 1

 |
|PageSize|Integer|No|10| Optional. The number of entries per page in the case of a paged query result. Maximum value: 50. Default value: 10

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ExpressCloudConnectionSet| | | The details of the returned ECC instances.

 |
|ApplicationBandwidth|String|3| The bandwidth set in the application for an ECC instance.

 |
|ApplicationId|String|1557820353902123884| The ID of the application.

 |
|ApplicationStatus|String|Initial| The status of the application.

 |
|ApplicationType|String|Create| The type of the application.

 |
|Bandwidth|Integer|10| The bandwidth of the ECC instance. Unit: Mbit/s.

 Valid values: **2 | 4 | 6 | 8 | 10 | 20 | 50 | 100 | 200 | 500 | 1000 | 10000 | 40000**

 |
|BusinessStatus|String|Normal| The service status of the ECC instance.

 |
|ChargeType|String|Prepaid| The billing method of the ECC instance.

 |
|CircuitCode|String|longtel001| The leased line code of the ECC instance.

 |
|ContactMail|String|XXX@example.com| The email of the person who applies for the ECC service.

 |
|ContactTel|String|132\*\*\*\*\*\*\*\*| The telephone number of the person who applies for the ECC service.

 |
|Description|String|ecc| The description of the ECC instance.

 The description must be 2 to 256 characters in length and must start with an English letter or a Chinese character. It cannot start with `http://` or `https://`.

 |
|Distance|Integer|100| The distance from the on-premises data center to the access point.

 |
|EndTime|String|2019-02-25T11:01:04Z| The time when the ECC instance expires.

 |
|GmtCreate|String|2019-05-14T15:52Z| The time when the ECC instance is created.

 |
|GmtModify|String|2019-05-14T16:52Z| The time when the ECC instance is modified.

 |
|HasReservationData|String|true| Indicates whether a renewal is made for the ECC instance.

 |
|IDCardNo|String|321283201002102345| The ID card number of the person who applies for the ECC service.

 |
|IdcSP|String|CU| The service provider of the on-premises data center.

 |
|InstanceId|String|ecc-bp1t9osmuln1vxfpt6gy8| The ID of the ECC instance.

 |
|Isp|String|CU| The service provider of the leased line.

 |
|Name|String|doctest| The name of the ECC instance.

 The name must be 2 and 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character. It cannot start with `http://` or `https://`.

 |
|PeerCity|String|Hangzhou| The city where the on-premises data center is located.

 |
|PeerLocation|String|5/F, XX Building, XX District| The location of the on-premises data center.

 The location is detailed and includes which floor the on-premises data center is.

 |
|PortType|String|100Base-T| The port type of the physical connection. Valid values:

 -   100Base-T: 100M electrical ports
-   1000Base-T \(default\): 1 Gigabit electrical ports
-   1000Base-LX: 1 Gigabit single-mode optical ports \(10 km\)
-   10GBase-T: 10G electrical ports
-   10GBase-LR: 10G single-mode optical ports \(10 km\)

 |
|RedundantEccId|String|ecc-xxxxxx| The ID of the redundant ECC instance.

 |
|ReservationActiveTime|String|2019-02-25T11:01:04Z| The time when the renewal takes effect.

 |
|ReservationBandwidth|String|200| The bandwidth of the ECC instance after the renewal.

 |
|ReservationInternetChargeType|String|PayByBandwidth| The billing method of the ECC instance after the renewal.

 |
|ReservationOrderType|String|RENEW| The type of the renewal order.

 |
|Status|String|Initial| The status of the ECC instance.

 |
|Type|String|local| The type of the leased line.

 |
|VirtualBorderRouterModels| | | The details of Virtual Border Routers \(VBRs\).

 |
|AccessPointId|String|ap-xxxx| The access point.

 |
|InstanceId|String|vbr-xxxx| The instance ID of the VBR.

 |
|PhysicalConnectionId|String|pc-xxxx| The instance ID of the physical connection.

 |
|PageNumber|Integer|2| The page number in the case of a paged query result.

 |
|PageSize|Integer|3| The number of entries per page in the case of a paged query result.

 |
|RequestId|String|6BF11256-9725-4C07-95F9-EF0F32B687E8| The ID of the request.

 |
|TotalCount|Integer|10| The total number of entries.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeExpressCloudConnections
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeExpressCloudConnectionsResponse>
	  <TotalCount>1</TotalCount>
	  <ExpressCloudConnectionSet>
		    <ExpressCloudConnectionType>
			      <HasReservationData>false</HasReservationData>
			      <Type></Type>
			      <ServiceProvider></ServiceProvider>
			      <InstanceId>ecc-bp1t9osmuln1vxfpt6gy8</InstanceId>
			      <IdcSP>CU</IdcSP>
			      <ApplicationId>1557820353902123884</ApplicationId>
			      <BusinessStatus>Normal</BusinessStatus>
			      <ApplicationBandwidth>3</ApplicationBandwidth>
			      <ContactMail>XX@example.com</ContactMail>
			      <ContactTel>13222312121</ContactTel>
			      <PortType>100Base-T</PortType>
			      <Bandwidth>3</Bandwidth>
			      <GmtModify></GmtModify>
			      <ChargeType></ChargeType>
			      <ApplicationType>Create</ApplicationType>
			      <Description>ecc</Description>
			      <IDCardNo>321283201002102345</IDCardNo>
			      <PeerCity>Hangzhou</PeerCity>
			      <GmtCreate>2019-05-14T15:52Z</GmtCreate>
			      <PeerLocation>XXX-XX Building--XX District</PeerLocation>
			      <Name>doctest</Name>
			      <CircuitCode></CircuitCode>
			      <Status>Initial</Status>
			      <RedundantEccId></RedundantEccId>
			      <Isp></Isp>
			      <ApplicationStatus>Initial</ApplicationStatus>
			      <VirtualBorderRouterModels></VirtualBorderRouterModels>
			      <EndTime></EndTime>
		    </ExpressCloudConnectionType>
	  </ExpressCloudConnectionSet>
	  <PageSize>10</PageSize>
	  <PageNo>1</PageNo>
	  <RequestId>6BF11256-9725-4C07-95F9-EF0F32B687E8</RequestId>
	</DescribeExpressCloudConnectionsResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"TotalCount":1,
	"PageSize":10,
	"ExpressCloudConnectionSet":{
		"ExpressCloudConnectionType":[
			{
				"HasReservationData":false,
				"ServiceProvider":"",
				"Type":"",
				"InstanceId":"ecc-bp1t9osmuln1vxfpt6gy8",
				"ApplicationId":"1557820353902123884",
				"IdcSP":"CU",
				"BusinessStatus":"Normal",
				"ApplicationBandwidth":3,
				"ContactMail":"XX@example.com",
				"ContactTel":"13222312121",
				"PortType":"100Base-T",
				"GmtModify":"",
				"Bandwidth":3,
				"ChargeType":"",
				"ApplicationType":"Create",
				"Description":"ecc",
				"IDCardNo":"321283201002102345",
				"PeerCity":"Hangzhou",
				"GmtCreate":"2019-05-14T15:52Z",
				"PeerLocation": "Fifth Floor, XX Building, XX District ",
				"Name":"doctest",
				"CircuitCode":"",
				"Status":"Initial",
				"RedundantEccId":"",
				"Isp":"",
				"ApplicationStatus":"Initial",
				"VirtualBorderRouterModels":{
					"VirtualBorderRouterModel":[]
				},
				"EndTime":""
			}
		]
	},
	"RequestId":"6BF11256-9725-4C07-95F9-EF0F32B687E8",
	"PageNo":1
}
```

## Errors {#section_dpy_v45_hc6 .section}

