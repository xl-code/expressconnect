# ConnectRouterInterface {#reference_1i4w_xmt_ndb .reference}

Connects the initiator router interface to the acceptor router interface.

After you call this action, the router interface status changes to Connecting. After the connection is established, the router interface status changes to Active.

Note the following before you call this action:

-   Only an initiator router interface in the Idle state can initiate a connection.

-   Up to one pair of interconnected router interfaces can be created between any two routers.

-   If there is an overdue router interface under the account, you cannot initiate a connection.


## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ConnectRouterInterface| The name of this action. Value: 

 ConnectRouterInterface

 |
|RegionId|String|Yes|cn-hangzhou| The region where the router interface is located.

 To query the region ID, call DescribeRegions.

 |
|RouterInterfaceId|String|Yes|ri-2zeo3xzyf38r4urzdpvfs| The ID of initiator router interface.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://vpc.aliyuncs.com/?Action=ConnectRouterInterface
&RegionId= cn-hangzhou
&RouterInterfaceId=ri-2zeo3xzyf38r4urzdpvfs
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <ConnectRouterInterfaceResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </ConnectRouterInterfaceResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_lxs_fvg_qgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our record.|The specified router interface does not exist.|
|400|IncorrectRole.NotInitiatingSide|The specified RouterInterface is not InitiatingSide.|This router interface is not the initiator router interface. Select the initiator router interface to initiate a connection.|
|400|Forbidden.OnlyOneConnection|The Specified routers have a connection already|A peering connection already exists between the routers.|
|400|Forbidden.OnlyOneConnection|Cannot connect concurrently between same routers|You cannot initiate another connection between the same routers.|
|400|Forbidden.BillsOutstanding|You cannot use this action because you have bills outstanding.|You cannot continue with this operation because you have overdue payments.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

