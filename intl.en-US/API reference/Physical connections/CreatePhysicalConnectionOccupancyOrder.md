# CreatePhysicalConnectionOccupancyOrder {#doc_api_Vpc_CreatePhysicalConnectionOccupancyOrder .reference}

Creates an order for the initial installation fee.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnectionOccupancyOrder) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreatePhysicalConnectionOccupancyOrder| The name of this action.

 Value: **CreatePhysicalConnectionOccupancyOrder**

 |
|PhysicalConnectionId|String|Yes|pc-bp1hp0wr072f6ambni141| The instance ID of the physical connection.

 |
|RegionId|String|Yes|cn-hangzhou| The region of the physical connection.

 |
|AutoPay|Boolean|No|true| Optional. Indicates whether to pay automatically. Valid values:

 -   true \(default value\): Automatic payment is enabled. Make sure that your account balance is sufficient. If the balance is insufficient, an abnormal order will be generated, which can only be voided.
-   false: Automatic payment is disabled.

 |
|ClientToken|String|No|CBCE910E-D396-4944-8764-B4047838B2D1| Optional. The client token used for authentication.

 |
|InstanceChargeType|String|No|PostPaid| Optional. The billing method of the physical connection. Valid values:

 -   PrePaid: Subscription. Make sure that your registered credit card is valid or you have sufficient balance in your PayPal account.
-   PostPaid \(default\): Pay-As-You-Go.

 |
|Period|Integer|No|1| Optional. The validity period of Subscription.

 |
|PricingCycle|String|No|Month| Optional. The unit cycle of Subscription.

 -   Year
-   Month

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CBCE910E-D396-4944-8764-B4047838B2D1| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreatePhysicalConnectionOccupancyOrder
&PhysicalConnectionId=pc-bp1hp0wr072f6ambni141
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreatePhysicalConnectionOccupancyOrderResponse>
  <code>200</code>
  <data>
    <orderId>203167309740138</orderId>
  </data>
  <httpStatusCode>200</httpStatusCode>
  <message>successful</message>
  <requestId>CBCE910E-D396-4944-8764-B4047838B2D1</requestId>
  <success>true</success>
</CreatePhysicalConnectionOccupancyOrderResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"message":"successful",
	"httpStatusCode":200,
	"requestId":"CBCE910E-D396-4944-8764-B4047838B2D1",
	"data":{
		"orderId":203167309740138
	},
	"code":"200",
	"success":true
}
```

## Error codes {#section_wlr_fpw_uw8 .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|The specified physical connection does not exist.|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|The request cannot be processed because the status of the resource does not permit this action.|

