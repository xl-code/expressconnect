# TerminatePhysicalConnection {#reference_i4w_xmt21_ndb .reference}

Terminate the access of the physical connection after the physical connection is enabled. The physical connection changes to the Terminating status after the API is called and changes to the Terminated status when the process is completed.

Note the following before terminating a physical connection:

-   You can only terminate a physical connection in the Enabled status.

-   Before terminating a physical connection, you must delete the Virtual Border Routers \(VBRs\) associated with the physical connection.


## Request parameters {#section_cch_pjg_mdb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
| Action |String|Yes| The action to perform. Valid value: 

  TerminatePhysicalConnection 

 |
| RegionId |String|Yes| The region of the physical connection.

 You can obtain the region ID by calling the DescribeRegions API.

 |
| PhysicalConnectionId |String|Yes| The ID of the physical connection.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
| RequestId |String|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

 **Request example** 

``` {#createVPCpub}
https://vpc.aliyuncs.com/?Action=TerminatePhysicalConnection
&PhysicalConnectionId=pc-2zeoaxkq3xxxxx
&RegionId=cn-beijing
&CommonParameters
```

 **Response example** 

XML format

```
<? xml version="1.0" encoding="UTF-8"? >

  "RequestId": "513E0A50-4F2D-4CBE-BF35-40559DF65D79"

```

