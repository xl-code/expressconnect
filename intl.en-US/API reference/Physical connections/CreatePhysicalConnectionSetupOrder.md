# CreatePhysicalConnectionSetupOrder {#doc_api_Vpc_CreatePhysicalConnectionSetupOrder .reference}

Creates an order for the resource occupation fee.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnectionSetupOrder) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|AccessPointId|String|Yes|ap-cn-beijing-ft-A| The ID of the access point.

 |
|Action|String|Yes|CreatePhysicalConnectionSetupOrder| The name of this action.

 Value: **CreatePhysicalConnectionSetupOrder**

 |
|LineOperator|String|Yes|CT| The service provider that provides the leased line. Valid values:

 -   CT: China Telecom
-   CU: China Unicom
-   CM: China Mobile
-   CO: Other service providers in Mainland China
-   Equinix: Equinix
-   Other: Other service providers outside Mainland China

 |
|RegionId|String|Yes|cn-shanghai| The region of the physical connection. To query the region ID, call DescribeRegions.

 |
|AutoPay|Boolean|No|true| Optional. Indicates whether to pay the fee automatically.

 Valid values: **true | false**

 |
|ClientToken|String|No|318BB676-0A2B-43A0-9AD8-F1D34E93750F| Optional. The token used for client authentication.

 |
|PortType|String|No|100Base-T| Optional. The type of the physical connection port. Valid values:

 -   **100Base-T**: 100M electrical ports
-   **1000Base-T** \(default value\): 1 Gigabit electrical ports
-   **1000Base-LX**: 1 Gigabit single-mode optical ports \(10 km\)
-   **10GBase-T**: 10GE electrical ports
-   **10GBase-LR**: 10GE single-mode optical ports \(10 km\)

 |
|RedundantPhysicalConnectionId|String|No|pc-bp10zsv5ntpxxxxxxxxxx| Optional. The ID of the redundant physical connection. Its status must be **Allocated**, **Confirmed**, or **Enabled**.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|OrderId|String|202844382740728| The ID of the order.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? AccessPointId=ap-cn-beijing-ft-A
&LineOperator=CT
&RegionId=cn-shanghai
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreatePhysicalConnectionSetupOrderResponse>
  <code>200</code>
  <data>
    <orderId>203255400960138</orderId>
  </data>
  <httpStatusCode>200</httpStatusCode>
  <message>successful</message>
  <requestId>AA874147-4A58-41D4-95E2-F2FFDAF417A6</requestId>
  <success>true</success>
</CreatePhysicalConnectionSetupOrderResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"message":"successful",
	"httpStatusCode":200,
	"requestId":"AA874147-4A58-41D4-95E2-F2FFDAF417A6",
	"data":{
		"orderId":203255400960138
	},
	"code":"200",
	"success":true
}
```

## Error codes {#section_566_snm_7fr .section}

