# DescribeVirtualBorderRouters {#doc_api_Vpc_DescribeVirtualBorderRouters .reference}

Queries one or more Virtual Border Routers \(VBRs\).

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVirtualBorderRouters) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String |Yes|DescribeVirtualBorderRouters|The name of this action.

 Value: **DescribeVirtualBorderRouters**

 |
|RegionId|String|Yes|cn-shanghai|The ID of the region to which the VBR belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|Filter.N.Key|String|No|1|Optional. The filter key. Value range of N: 1 to 5

 |
|Filter.N.Value.N|RepeatList|No|1|Optional. The value of the filter key. Value range of N: 1 to 5.

 |
|PageNumber|Integer|No|10|Optional. The page number. Default value: 1

 |
|PageSize|Integer|No|1|Optional. The number of rows per page for a paged query. Maximum value: 50. Default value: 10

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VirtualBorderRouterSet| | |The list of VBRs.

 |
|AccessPointId|String|ap-cn-kojok1xxxxxxxx|The ID of the physical connection access point.

 |
|ActivationTime|String|2017-06-08T12:20:55|The time when the VBR is activated for the first time.

 |
|AssociatedCens| | |The associated CEN instances.

 |
|CenId|String|cen-kojok19xxxxxxxx|The ID of the CEN instance.

 |
|CenOwnerId|Long|1086496381294461|The UID of the account to which the CEN instance belongs.

 |
|CenStatus|String|Attached|The status of the CEN instance.

 |
|AssociatedPhysicalConnections| | |The associated physical connections.

 |
|CircuitCode|String|12|The leased line code provided by the service provider for the physical connection.

 |
|LocalGatewayIp|String|116.62.xx.xx|The Alibaba Cloud-side IP address used by the VBR.

 |
|PeerGatewayIp|String|116.62.xx.xx|The customer-side IP address used by the VBR.

 |
|PeeringSubnetMask|String|255.255.255.252|The subnet mask of the Alibaba Cloud-side IP address and customer-side IP address.

 |
|PhysicalConnectionBusinessStatus|String|Normal|The service status of the physical connection.

 |
|PhysicalConnectionId|String|pc-119mfjzm7xxxxxxxx|The ID of the physical connection.

 |
|PhysicalConnectionOwnerUid|String|qfrgrgs|The UID of the owner of the physical connection.

 |
|PhysicalConnectionStatus|String|Normal|The status of the physical connection.

 |
|VlanId|String|0|The VLAN ID of the VBR.

 |
|VlanInterfaceId|String|ri-kojok19x3j0q6kxxxxxxxxx|The ID of the physical connection interface. This interface can be used as the next hop of routes on the VBR.

 |
|CircuitCode|String|longtel001|The leased line code provided by the service provider for the physical connection.

 |
|CreationTime|String|2017-06-08T12:20:55|The time when the VBR is created.

 |
|Description|String|VBR|The description of the VBR.

 |
|DetectMultiplier|Long|3|The multiplier of the detection time. Specifically, the maximum number of discarded connection packets that the receiver allows from the sender. Value range: 3 to 10

 |
|LocalGatewayIp|String|116.62.xx.xx|The Alibaba Cloud-side IP address used by the VBR.

 |
|MinRxInterval|Long|100|The time interval between two consecutive BFD packets that are received. Value range: 200 to 1000. Unit: ms

 |
|MinTxInterval|Long|100|The time interval between two consecutive BFD packets that are sent. Value range: 200 to 1000. Unit: ms

 |
|Name|String|test|The name of the VBR.

 |
|PeerGatewayIp|String|116.62.xx.xx|The customer-side IP address used by the VBR.

 |
|PeeringSubnetMask|String|255.255.255.252|The subnet mask of the Alibaba Cloud-side IP address and the customer-side IP address.

 |
|PhysicalConnectionBusinessStatus|String|Normal|The service status of the physical connection.

 |
|PhysicalConnectionId|String|pc-119mfjzm7xxxxxxxx|The ID of the physical connection to which the VBR belongs.

 |
|PhysicalConnectionOwnerUid|String|usdgbh123fvgf|The UID of the owner of the physical connection.

 |
|PhysicalConnectionStatus|String|Normal|The status of the physical connection.

 |
|RecoveryTime|String|2017-06-08T12:20:55|The most recent time when the VBR is recovered from the Terminated state to the Active state.

 |
|RouteTableId|String|rtb-bp1nxxxxxxxxxxxxxxxx|The ID of the route table of the VBR.

 |
|Status|String|active|The status of the physical connection:

 -   Initial: Indicates that the physical connection is being applied.
-   Approved: Indicates that the physical connection application is approved.
-   Allocating: Indicates that resources are being allocated.
-   Allocated: Indicates that cables are being installed at the data center.
-   Confirmed: Indicates that the physical connection is waiting for user confirmation.
-   Enabled: Indicates that the physical connection is enabled.
-   Rejected: Indicates that the physical connection application is rejected.
-   Canceled: Indicates that the physical connection is canceled.
-   Allocation Failed: Indicates that the resource allocation fails.
-   Terminated: Indicates that the physical connection is terminated.

 |
|TerminationTime|String|2017-06-08T12:20:55|The most recent time when the VBR is terminated.

 |
|VbrId|String|vbr-kojok19xxxxxxxxx|The ID of the VBR.

 |
|VlanId|Integer|10|The VLAN ID of the VBR.

 |
|VlanInterfaceId|String|ri-2zeo3xzyf38r4xxxxxxxx|The ID of the router interface of the VBR.

 |
|TotalCount|Integer|10|The number of queried VBRs.

 |
|PageNumber|Integer|10|The current page number.

 |
|PageSize|Integer|10|The number of VBRs per page.

 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeVirtualBorderRouters
&RegionId=cn-shanghai
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeVirtualBorderRoutersResponse>
  <RequestId>AE65530E-8436-4FB1-8217-DCD35712AC89</RequestId>
  <PageNumber>1</PageNumber>
  <VirtualBorderRouterSet>
    <VirtualBorderRouterType>
      <LocalGatewayIp>10.1.xx.xx</LocalGatewayIp>
      <PeerGatewayIp>10.2.xx.xx</PeerGatewayIp>
      <PhysicalConnectionOwnerUid>123157908XXXXXXXX</PhysicalConnectionOwnerUid>
      <VlanId>10</VlanId>
      <PhysicalConnectionStatus>Enabled</PhysicalConnectionStatus>
      <PhysicalConnectionId>pc-2zeoaxkq3jotxxxxxxxx</PhysicalConnectionId>
      <RouteTableId>vtb-2ze9hmd6yofwvxxxxxxxx</RouteTableId>
      <PeeringSubnetMask>255.0.0.0</PeeringSubnetMask>
      <CreationTime>2018-03-06T11:16:34Z</CreationTime>
      <ActivationTime>2018-03-06T11:16:34Z</ActivationTime>
      <Status>active</Status>
      <PhysicalConnectionBusinessStatus>Normal</PhysicalConnectionBusinessStatus>
      <VlanInterfaceId>ri-2zeum6rgu0586xxxxxxxx</VlanInterfaceId>
      <AccessPointId>ap-cn-beijing-dx-A</AccessPointId>
      <VbrId>vbr-2zecmmvg5gxxxxxxxx</VbrId>
    </VirtualBorderRouterType>
  </VirtualBorderRouterSet>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
</DescribeVirtualBorderRoutersResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"DescribeVirtualBorderRoutersResponse":{
		"PageNumber":"1",
		"VirtualBorderRouterSet":{
			"VirtualBorderRouterType":{
				"LocalGatewayIp":"10.1.xx.xx",
				"PeerGatewayIp":"10.2.xx.xx",
				"PhysicalConnectionOwnerUid":"123157908XXXXXXXX",
				"VlanId":"10",
				"PhysicalConnectionStatus":"Enabled",
				"PhysicalConnectionId":"pc-2zeoaxkq3jotxxxxxxxx",
				"RouteTableId":"vtb-2ze9hmd6yofwvxxxxxxxx",
				"PeeringSubnetMask":"255.0.0.0",
				"CreationTime":"2018-03-06T11:16:34Z",
				"ActivationTime":"2018-03-06T11:16:34Z",
				"Status":"active",
				"PhysicalConnectionBusinessStatus":"Normal",
				"VlanInterfaceId":"ri-2zeum6rgu0586xxxxxxxx",
				"VbrId":"vbr-2zecmmvg5gxxxxxxxx",
				"AccessPointId":"ap-cn-beijing-dx-A"
			}
		},
		"TotalCount":"1",
		"PageSize":"10",
		"RequestId":"AE65530E-8436-4FB1-8217-DCD35712AC89"
	}
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message |Description|
|----------------|----------|--------------|-----------|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|The specified filter key is not supported.|

