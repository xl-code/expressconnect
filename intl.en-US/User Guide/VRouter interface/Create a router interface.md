# Create a router interface {#task_hqt_sty_xdb .task}

A router interface of Express Connect is a virtual device used to establish a communication channel and control the working status. Express Connect abstracts the process of building an intranet communication channel between two VPCs by creating a router interface on each of the two VRouters respectively and connecting the router interfaces, so that both VRouters can send messages to each other through the channel. You can create router interfaces to connect two VPCs, or connect a VBR with a VPC through physical access to connect an on-premises IDC to the VPC.

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri). 
2.  In the left-side navigation pane, select **VPC Connection** \> **Router Interface**. 
3.  In the upper-right corner of the router interface page, click **Create Router Interface**. 
4.  Configure the router interface according to the following information, and complete the payment. 

    |Configuration|Description|
    |:------------|:----------|
    |**Billing method**|Select a billing method. For more information, see [Billing](../../../../reseller.en-US/Pricing/Billing of physical connections.md#).|
    |**Scenario**|Select the scenario for the router interface:    -   **VPC Interconnect**: Connect two VPCs.
    -   **Physical Access**: Connect a VPC to the VBR of a leased line.
|
    |**Router Creation**|When two router interfaces are interconnecting, one plays the role of the connection initiator and the other plays the role of the connection receiver. The initiator and receiver are only used to control the process of establishing connections. In actual network communication, the communication link is bidirectional and there is no difference between the initiator and receiver.For VPC interconnection or physical access under the same account, select **Create Initiator and Receiver**.

For VPC interconnection or physical access under different accounts, select **Create Initiator** or **Create Receiver** as needed.

In the scenario of physical access, the VBR can act only as the initiator.

|
    |**Local Region**|Select the region where the VPC or VBR is located.|
    |**VPC ID**|Select the VPC to be connected.**Note:** In the scenario of **Create Initiator and Receiver**, the local VPC is the connection initiating end.

|
    |**Access Point**|Select the access point of the leased line associated with the VBR.**Note:** This option is only applicable to physical access.

|
    |**VBR ID**|Select the VBR to be connected.**Note:** This option is only applicable to physical access.

|
    |**Peer Region**|Select the region where the peer VPC is located.|
    |**Peer VPC ID**|Select the ID of the Peer VPC.|
    |**Specification**|Select the specification of the initiator router interface as needed and the receiver router interface will automatically use the same specification as the initiator.|


