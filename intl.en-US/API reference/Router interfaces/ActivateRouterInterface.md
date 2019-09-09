# ActivateRouterInterface {#reference_i94w_xmt_ndb .reference}

Activates a router interface in the Inactive state.

After you call this action, the router interface changes to the Activating state. Next, after activation is completed, the router interface changes to the Active state.

**Note:** An overdue interface cannot be activated.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ActivateRouterInterface| The name of this action. Value: 

 ActivateRouterInterface

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the router interface to be activated belongs.

 To query the region ID, call DescribeRegions.

 |
|RouterInterfaceId|String|Yes|ri-2zeo3xzyf38r4urzdpvfs| The ID of the router interface to be activated.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameters|Type|Example value|Description|
|:---------|:---|-------------|:----------|
|RequestId|String|079874CD-AEC1-43E6-AC03-ADD96B6E4907|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://vpc.aliyuncs.com/?Action=ActivateRouterInterface
&RegionId=cn-hangzhou
&RouterInterfaceId=ri-2zeo3xzyf38r4urzdpvfs
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <ActivateRouterInterfaceResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </ActivateRouterInterfaceResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_zrp_yzg_qgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our records.|The specified router interface does not exist.|
|400|IncorrectStatus|RouterInterface can be operated by this action only when it's status is Inactive.|This operation requires that the router interface is in the Inactive status.|
|400|Forbidden.FinancileLocked|This RouterInterface is financiel locked because of bills outstanding.|The router interface is locked due to an insufficient account balance.|
|400|Forbbiden|The Router instance owener error|This router does not belong to your account.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

