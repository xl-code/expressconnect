# Interconnect a VPC and a VBR {#task_j2d_hk3_dfb .task}

You can fulfill intercommunication between a VPC and a Virtual Border Router \(VBR\) by creating a peering connection.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**. 
3.  Click **Create Peering Connection**.
4.  Configure the peering connection. 

    |Configuration|Descripition|
    |:------------|:-----------|
    |**Account Type**| Select whether the VPC and the VBR you want to connect belong to the same account.

    -   **Same as Peer's**: If the VPC and VBR to be connected belong to the same account, the system creates an initiator instance and an acceptor instance at the same time, and automatically establishes a connection between them.
    -   **Different from Peer's**: If the VPC and VBR to be connected belong to different accounts, you need to create an initiator instance and an acceptor instance respectively before initiating the connection from the initiator instance.
 |
    |**Connection Type**| Select the peering connection type:

    -   **VPC-to-VPC**: Establish a peering connection between two VPCs.
    -   **VBR-to-VPC**: Establish a peering connection between a VPC and a VBR.

In this example, select **VBR-to-VPC**.

 |
    |**Routers to Create**|Select the instances to be created:    -   **Initiator and Acceptor**: Both an initiator instance and an acceptor instance are created. After the creation, the initiator instance automatically connects to the acceptor instance.

This option applies only to connections under the same account.

    -   **Initiator Only**: The initiator instance is created and the initiator instance can initiate the connection actively.

If VBR-to-VPC is selected for the connection type, only VBR is available for the route type of the initiator.

This option applies only to connections between different accounts.

    -   **Acceptor Only**: An acceptor instance is created.

Only VPC is available for the acceptor router type.

This option applies only to connections between different accounts.

|
    |**Local Region**|Select the region of the VBR.|
    |**Local Access Point**|Select the access point to which the VBR connects.|
    |**Local VBR ID**|Select the VBR to which you want to establish the connection.|
    |**Peer Region**|Select the region of the peer VPC.|
    |**Peer VPC ID**|Select the ID of the peer VPC.|
    |**Bandwidth**|Select a bandwidth for the connection.Use the default bandwidth for the acceptor instance.

|
    |**Validity**|Select a validity period for your subscription.If you want the subscription to automatically renew when it expires, select **Auto Renew**.

|


