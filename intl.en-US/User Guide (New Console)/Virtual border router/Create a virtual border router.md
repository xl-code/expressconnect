# Create a virtual border router {#task_jqm_hqx_dfb .task}

After establishing a physical connection, you need to create a Virtual Border Router \(VBR\) for the leased line as a forwarding bridge for data from the VPC to your local IDC.

VBR is a router between the VPC and the Custom-Premises Equipment \(CPE\) in your local IDC. VBR has a route table. You can configure route entries in the route table to forward traffic. VBR provides the following functions:

-   Exchanges data packets as an intermediate router between the VPC and the local IDC.
-   Decides the port mode of the physical connection: Layer-3 route interface mode or VLAN-based Layer-3 sub-interface mode.
-   Attaches or identifies VLAN tags in Layer-3 sub-interface mode.
-   Supports BGP dynamic routing.

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**. 
3.  Click **Create VBR**. 
4.  Configure the VBR, and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Belongs to Current Account**|Create a VBR for all physical connections under the same account or a different account.|
    |**Account**| If you want to create a VBR for the physical connections under a different account, enter the account ID of the physical connection owner.

 |
    |**VLAN ID**|Enter the VLAN ID of the VBR, ranging from 0 to 2999.    -   When the VLAN ID is 0, it indicates that the switch port of the VBR uses Layer-3 route interface mode instead of VLAN mode. In Layer-3 route interface mode, each physical connection corresponds to a VBR.
    -   When the VLAN ID is a value from 1 to 2999, it indicates that the switch port of the VBR uses VLAN-based Layer-3 sub-interface mode. In Layer-3 sub-interface mode, each VLAN ID corresponds to a VBR. In this mode, the physical connection of the VBR can connect the VPCs under multiple accounts. The VBRs of different VLANs are isolated from one another by the Layer-2 network.
For example, a company has multiple subdivisions or subsidiaries. Each has an independent Alibaba Cloud account, and each account has an independent VPC. If the company applies for a physical connection, it needs to plan a VLAN ID for each subdivision or subsidiary. When creating router interfaces, the company uses VLAN IDs to identify the subsidiaries or subdivisions that use the physical connection, isolating them from each other by using the Layer-2 network.

|
    |**Gateway IP Address on Alibaba Cloud Side**|Enter the IP address of the gateway from the VPC to your local IDC.|
    |**Gateway IP Address on Customer Side**|Enter the IP address of the gateway from your local IDC to the VPC.|
    |**Subnet Mask**|Enter the subnet mask of the gateway IP address on the Alibaba Cloud side and the gateway IP address on the customer side. Only two IP addresses are required. Therefore, you can enter a longer subnet mask.|


