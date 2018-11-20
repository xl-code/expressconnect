# Add route entries {#task_yjg_psx_dfb .task}

VBR has a route table. You can configure route entries in the route table to forward traffic.

In the VBR, you must add one route entry directed to the physical connection and another route entry directed to the VPC to forward the traffic of the VPC and the local IDC, respectively. VBR allows you to configure BGP routing for the local IDC. For more information, see [Configure BGP](reseller.en-US/User Guide (New Console)/Virtual border router/Configure BGP.md#).

When you manage the route entries of VBR, pay attention to the following restrictions:

-   Each route table supports 48 custom route entries.
-   Source address policy routing is not supported.

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**. 
3.  Select the region of the VBR and then click the VBR ID. 
4.  Click the **Route Entries** tab and then click **Add Route Entry**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21430/154272712912048_en-US.png)

5.  Configure the route entry and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Destination Subnet**|Enter the destination subnet.|
    |**Next Hop Type**| Select the type of the next hop:

    -   **VPC**: Forwards data to the selected VPC.
    -   **Physical Connection Interface**: Forwards data to the selected physical connection interface.
 |
    |**Next Hop**|Select the next hop instance that receives the data, based on the next hop type.|


