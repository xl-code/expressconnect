# Interconnect two VPCs {#task_j2d_hk3_dfb .task}

You can interconnect two VPCs by creating a peering connection between them.

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。 
2.  In the left navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**. 
3.  Click **Create Peering Connection**. 
4.  Configure the peering connection. 

    |Configuration item|Description|
    |:-----------------|:----------|
    |**Belong to Same Account**| Select whether the VPCs you want to connect belong to the same account or different accounts.

    -   **Yes**: If the VPCs to be connected belong to the same account, the system creates both the initiator instance and the acceptor instance simultaneously, and establishes the connection automatically.
    -   **No**: If the VPCs to be connected belong to different accounts, you need to create the initiator instance and the acceptor instance respectively before the connection is initiated by the initiator instance.
 |
    |**Connection Type**| Select a peering connection type:

    -   **VPC-to-VPC**: Establish a peering connection between two VPCs.
    -   **VBR-to-VPC**: Establish a peering connection between a VPC and a VBR. For more information, see [Interconnect a VPC and a VBR](intl.en-US/User Guide/Peering connection/Interconnect a VPC and a VBR.md#).
 In this example, select **VPC-to-VPC**.

 |
    |**Router Creation**|Select the type of the instance to be created:    -   **Create Initiator and Acceptor**: Both the initiator instance and the acceptor instance are created simultaneously. After creation, the initiator instance automatically connects to the acceptor instance.

This option applies only to connections within the same account.

    -   **Create Initiator**: The initiator instance is created and the initiator instance can initiate the connection actively.

The router type of the initiator instance can be VPC or VBR. If the peering connection type is selected as VBR-to-VPC, only VBR is available for the router type of the initiator instance.

This option applies only to connections between different accounts.

    -   **Create Acceptor**: The acceptor instance is created.

Only VPC is available for the router type of the acceptor instance.

This option applies only to connections between different accounts.

|
    |**VPC ID**|Select the VPC of the local end \(the initiator end of the connection or the acceptor end\).|
    |**Local Region**|Select the region of the local VPC.|
    |**Peer VPC ID**|Select the VPC of the peer end \(the initiator end of the connection or the acceptor end\).|
    |**Peer Region**|Select the region of the peer VPC.|
    |**Bandwidth**|Select the bandwidth for the connection.Use the default bandwidth for the acceptor instance.

|
    |**Order Time**|Select the subscription duration.If you want automatic renewal after expiration, select the **Auto Renew** check box.

|


