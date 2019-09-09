# ModifyRouterInterfaceAttribute {#refere8nce_i4w_xmt_ndb .reference}

Modifies the configurations of a router interface.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyRouterInterfaceAttribute| The name of this action. Value: 

 ModifyRouterInterfaceAttribute

 |
|RegionId|String|Yes|cn-shanghai| The ID of the region to which the router interface belongs.

 To query the region ID, call DescribeRegions.

 |
|RouterInterfaceId|String|Yes|ri-2zeo3xzyf38r4urzdpvfs| The ID of the router interface.

 |
|DeleteHealthCheckIp|Boolean|No|true| Indicates whether to delete the health check IP address configured on the router interface.  Valid values: 

 -   true: Delete the health check IP.

-   false\(default value\): Do not delete the health check IP.


 |
|Description|String|No|Router inteface 1| The description of the router interface.

 The description must be 2 to 256 characters in length. The description must start with a letter and cannot start with `http://` or `https://`.

 |
|HealthCheckSourceIp|String|No|116.62.222.28| The source IP address used to perform health check on the physical connection. It must be an unused IP address of the local VPC.

 **Note:** You can specify this parameter in the scenario of physical access.

 |
|HealthCheckTargetIp|String|No|116.62.222.28| The destination IP address of health check.

 **Note:** This parameter is required when the HealthCheckSourceIp parameter is specified.

 |
|Name|String|No|TEST| The name of the router interface.

 The name must be 2 to 128 characters in length. It can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with `http://`  or `https://`.

 |
|OppositeInterfaceId|String|No|ri-2zeo3xzyf38r4urzdpvfs| The ID of the peer router interface.

 |
|OppositeInterfaceOwnerId|String|No|10| The ID of the owner of the peer router interface.

 |
|OppositeRouterId|String|No|vrt-bp1jcg5cmxjbl9xgc58bw| The ID of the peer router.

 |
|OppositeRouterType|String|No|VRouter| The type of the router to which the peer router interface belongs. The default value is VBR.

 Valid values:VRouter|VBR

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://vpc.aliyuncs.com/?Action=ModifyRouterInterfaceAttribute
&RegionId=cn-shanghai
&RouterInterfaceId=ri-2zeo3xzyf38r4urzdpvfs
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <ModifyRouterInterfaceAttributeResponse>
      <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
    </ModifyRouterInterfaceAttributeResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"980960B0-2969-40BF-8542-EBB34FD358AB"
    }
    ```


## Error codes {#section_y4z_4nh_qgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our records.|The specified router interface does not exist.|
|400|Forbidden.FinancileLocked|This RouterInterface is financiel locked because of bills outstanding.|The router interface is locked due to an insufficient account balance.|
|400|InvalidName.Malformd|The attribute name is illeagl.|The name format is invalid.|
|400|InvalidOppositeRouterType.ValueNotSupported|The specified OppositeRouterType is not valid.|The value of the OppositeRouterType parameter is invalid.|
|400|InvalidDescription.Malformed|The Description is illeagl.|The format of the resource description is invalid. The description must be 2 to 256 characters in length, and it cannot start with http:// and https://.|
|400|Forbbiden|The Router instance owener error|The specified router is not under your account.|
|400|LinkRole.NotSupport|This linkrole is not supported|This link is not supported.|
|400|InvalidParam.ModifyRouterInterface|Modify routerinterface param invalide|The entered parameter is invalid.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

