# Interconnect a VPC and a VBR {#task_j2d_hk3_dfb .task}

You can fulfill intercommunication between a VPC and a Virtual Border Router \(VBR\) by creating a peering connection.

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。 
2.  In the left navigation pane, click **VPC Peering Connections** \> **VBR-to-VPC**. 
3.  Click **Create Peering Connection**.
4.  Configure peering connections. 

    |Configuration item|Description|
    |:-----------------|:----------|
    |**Belong to Same Account**| Select whether the VPC and VBR you want to connect belong to the same account or different accounts.

    -   **Yes**: If the VPC and VBR to be connected belong to the same account, the system creates an initiator instance and an acceptor instance at the same time, and automatically establishes a connection.
    -   **No**: If the VPC and VBR to be connected belong to different accounts, you need to create an initiator instance and an acceptor instance respectively before initiating the connection from the initiator instance.
 |
    |**Connection Type**| Select a peering connection type:

    -   **VPC-to-VPC**: Establish a peering connection between two VPCs.
    -   **VBR-to-VPC**: Establish a peering connection between a VPC and a VBR.

In this example, select **VBR-to-VPC**.

 |
    |**Routers to Create**|Select the type of the instance to be created:    -   **Initiator and Acceptor Routers**: Both the initiator instance and the acceptor instance are created. After creation, the initiator instance automatically connects to the acceptor instance.

This option applies only to connections with the same account.

    -   **Initiator Router Only**: The initiator instance is created and the initiator instance can initiate the connection actively.

If VBR-to-VPC is selected for the connection type, only VBR is available for the route type of the initiator.

This option applies only to connections between different accounts.

    -   **Acceptor Router Only**: The acceptor instance is created.

Only VPC is available for the acceptor router type.

This option applies only to connections between different accounts.

|
    |**Region**|Select the region of the VBR.|
    |**Access Point**|Select the access point to which the VBR connects.|
    |**Initiator VBR ID**|Select the VBR to which you want to establish the connection.|
    |**Acceptor Region**|Select the region of the VPC.|
    |**Acceptor VPC ID**|Select the ID of the VPC.|
    |**Bandwidth**|Select a bandwidth for the connection.Use the default bandwidth for the acceptor instance.

|
    |**Validity**|Select the subscription duration.If you want automatic renewal after expiration, check the **Auto Renew** check box.

|


