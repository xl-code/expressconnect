# DescribeVirtualBorderRoutersForPhysicalConnection {#doc_api_1088689 .reference}

Queries the Virtual Border Routers \(VBRs\) associated with a physical connection, including the VBRs under the physical connection owner's account and other accounts.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVirtualBorderRoutersForPhysicalConnection) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVirtualBorderRoutersForPhysicalConnection| The name of this action.

 Value: **DescribeVirtualBorderRoutersForPhysicalConnection**

 |
|PhysicalConnectionId|String|Yes|pc-119mfjzm7| The ID of the physical connection.

 |
|RegionId|String|Yes|cn-shanghai| The ID of the region to which the physical connection belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|Filter.N.Key|String|No|1| Optional. The filter key. Value range of N: 1 to 5.

 |
|Filter.N.Value.N|RepeatList|No|1| Optional. The value of the filter key. Value range of N: 1 to 5.

 |
|PageNumber|Integer|No|10| Optional. The page number of the VBR list. Default value: 1

 |
|PageSize|Integer|No|10| Optional. The number of rows per page. Maximum value: 50. Default value: 10

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VirtualBorderRouterForPhysicalConnectionSet| | | The list of VBRs.

 |
|└ActivationTime|String|2017-06-08T12:20:55| The time when the VBR is activated for the first time.

 |
|└CircuitCode|String|longtel001| The leased line code provided by the service provider for the physical connection.

 |
|└CreationTime|String|2017-06-08T12:20:55| The time when the VBR is created.

 |
|└LocalGatewayIp|String|10.0.0.4| The Alibaba Cloud-side IP address used by the VBR.

 |
|└PeerGatewayIp|String|10.0.0.5| The customer-side IP address used by the VBR.

 |
|└PeeringSubnetMask|String|255.255.255.0| The subnet mask of the Alibaba Cloud-side IP address and the customer-side IP address.

 |
|└RecoveryTime|String|2017-06-08T12:20:55| The most recent time when the VBR is recovered from the Terminated state to the Active state.

 |
|└TerminationTime|String|2017-06-08T12:20:55| The most recent time when the VBR is terminated.

 |
|└VbrId|String|12| The ID of the VBR.

 |
|└VbrOwnerUid|Long|1342435124| The account ID of the VBR owner. When the VBR and the physical connection belong to the same owner, this parameter is empty.

 |
|└VlanId|Integer|10| The VLAN ID of the VBR.

 |
|TotalCount|Integer|10| The total number of queried VBRs.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of queried VBRs per page.

 |
|RequestId|String|7C5AE8B3-A2D8-428D-A2FF-93A225C0821E| The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://vpc.aliyuncs.com/? Action=DescribeVirtualBorderRoutersForPhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<? xml version="1.0" encoding="UTF-8"? >
<DescribeVirtualBorderRoutersForPhysicalConnectionResponse>
	<RequestId>03E8CB87-5876-4034-BBB2-6E0851281C37</RequestId>
	<PageNumber>1</PageNumber>
	<TotalCount>2</TotalCount>
	<PageSize>10</PageSize>
	<VirtualBorderRouterForPhysicalConnectionSet>
		<VirtualBorderRouterForPhysicalConnectionType>
			<ActivationTime>2018-03-06T11:16:34Z</ActivationTime>
			<CreationTime>2018-03-06T11:16:34Z</CreationTime>
			<CircuitCode></CircuitCode>
			<VlanId>10</VlanId>
			<RecoveryTime></RecoveryTime>
			<VbrOwnerUxxx231579085529123</VbrOwnerUid>
			<TerminationTime></TerminationTime>
			<VbrId>Vbrxxxxx-2zecmmvg5gvu8i4telkhw</VbrId>
		</VirtualBorderRouterForPhysicalConnectionType>
		<VirtualBorderRouterForPhysicalConnectionType>
			<ActivationTime>2018-01-04T13:34:18Z</ActivationTime>
			<CreationTime>2018-01-04T13:34:18Z</CreationTime>
			<CircuitCode></CircuitCode>
			<VlanId>100</VlanId>
			<RecoveryTime></RecoveryTime>
			<VxxxbrOwnerUid>1231579085529123</VbrOwnerUid>
			<TerminationTime></TerminationTime>
			<VbrId>vbr-2zee2e2cwetx4k0tohakw</VbrId>
		</VirtualBorderRouterForPhysicalConnectionType>
</DescribeVirtualBorderRoutersForPhysicalConnectionResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"03E8CB87-5876-4034-BBB2-6E0851281C37",
	"VirtualBorderRouterForPhysicalConnectionSet":{
		"VirtualBorderRouterForPhysicalConnectionType":[
			{
				"CreationTime":"2018-03-06T11:16:34Z",
				"ActivationTime":"2018-03-06T11:16:34Z",
				"CircuitCode":"",
				"VlanId":10,
				"RecoveryTime":"",
				"VbrOwnerUid":"1231579085xxxxxx529123",
				"VbrId":"vbr-2zecmmvg5gvu8xxxxw",
				"TerminationTime":""
			},
			{
				"CreationTime":"2018-01-04T13:34:18Z",
				"ActivationTime":"2018-01-04T13:34:18Z",
				"CircuitCode":"",
				"VlanId":100,
				"RecoveryTime":"",
				"VbrOwnerUid":"1231579085xxx",
				"VbrId":"vbr-2zee2e2cwetx4k0txxxxakw",
				"TerminationTime":""
			}
		]
	}
}
```

## Error codes {#section_wwk_crx_v8s .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidPhysicalConnectionId.NotFound|The specified PhysicalConnectionId does not belong to user.|The specified physical connection does not belong to your account.|

[See common error codes.](https://error-center.aliyun.com/status/product/Vpc)

