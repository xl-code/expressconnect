# Interconnect two VPCs {#task_j2d_hk3_dfb .task}

You can interconnect two VPCs by creating a peering connection between them.

**Note:** If this is the first time that you use Express Connect to interconnect two VPCs, we recommend that you use Cloud Enterprise Network \(CEN\). For more information, see [Tutorial overview](../../../../../intl.en-US/Quick Start/Tutorial overview.md#).

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection. 

    |Configuration|Description|
    |:------------|:----------|
    |**Account type**| Select whether the VPCs you want to connect belong to the same account.

    -   **Same as Peer's**: If the VPCs to be connected belong to the same account, the system creates an initiator instance and an acceptor instance at the same time, and automatically establishes a connection between them.
    -   **Different from Peer's**: If the VPCs to be connected belong to different accounts, you must create an initiator instance and an acceptor instance separately before initiating the connection from the initiator instance.
 |
    |**Connection Type**| Select the peering connection type.

    -   **VPC-to-VPC**: Establish a peering connection between two VPCs.
    -   **VBR-to-VPC**: Establish a peering connection between a VPC and a VBR. For more information, see [Interconnect a VPC and a VBR](intl.en-US/Peering connections/Interconnect a VPC and a VBR.md#).
 In this example, select **VPC-to-VPC**.

 |
    |**Routers to Create**|Select the instances to be created.     -   **Initiator and Acceptor**: Both an initiator instance and an acceptor instance are created. After the creation, the initiator instance automatically connects to the acceptor instance.

This option applies only to connections under the same account.

    -   **Create Initiator**: An initiator instance is created and the initiator instance can initiate the connection actively.

The initiator router type can be VPC or VBR. If VBR-to-VPC is selected for the peering connection type, only VBR is available for the initiator router type.

This option applies only to connections between different accounts.

    -   **Acceptor Only**: An acceptor instance is created.

Only VPC is available for the acceptor router type.

This option applies only to connections between different accounts.

**Note:** Only Pay-As-You-Go billing supports creating an acceptor separately. The acceptor instance is free of charge.

 |
    |**Local VPC ID**|Select the ID of the local VPC \(the initiator or the acceptor of the connection\).|
    |**Local Region**|Select the region of the local VPC.|
    |**Peer VPC ID**|Select the ID of the peer VPC \(the initiator or the acceptor of the connection\).|
    |**Peer Region**|Select the region of the peer VPC.|
    |**Bandwidth**|Select a bandwidth value for the connection. Use the default bandwidth for the acceptor instance.

 |
    |**Validity**|Select a validity period for your subscription. If you want the subscription to automatically renew when it expires, select the **Auto Renew** check box.

 |


