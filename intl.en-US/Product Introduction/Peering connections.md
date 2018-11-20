# Peering connections {#concept_ymg_rry_xdb .concept}

You can establish a peering connection between two VPCs or between a VPC and a VBR.

## Initiator and acceptor {#section_lcr_v4q_ydb .section}

When you establish a peering connection, one end \(VPC or VBR\) of the connection is the initiator, and the other end is the acceptor. Only the initiator can initiate a connection. The acceptor can only wait for the initiator to initiate a connection. The initiator and the acceptor are only used to control the process of connection establishment. After the connection is established, the communication link is bidirectional and there is no difference between the initiator and the acceptor.

For interconnections between VPCs under the same account, Express Connect provides an option to create the initiator and the acceptor at the same time. You do not need to manually initiate the connection. The system will automatically initiate and establish the connection. For interconnections between VPCs under different accounts, you must manually initiate a connection.

The following table compares the initiator and acceptor.

|Item|Initiator|Acceptor|
|:---|:--------|:-------|
|Is this end charged when VPCs are interconnected in the same region?|No|No|
|Is this end charged when VPCs are interconnected between different regions?|Yes|No|
|Is it required to configure peer information before initiating a connection?|Yes|Yes|
|Can this end initiate a connection?|Yes|No|
|Can this end send messages to the peer end after a connection is established?|Yes|Yes|

## Connection process and status {#section_qcr_v4q_ydb .section}

In the peering connection process, the initiator initiates a connection. The acceptor then receives the connection, after which the connection is established successfully.

During different stages of the connection process, the status of a peering connection is also different, as shown in the following table.

**Note:** If you choose to create both ends at the same time when establishing a peering connection, the system automatically initiates and establishes a connection. In this case, the initiator and the acceptor become activated after being created.

|Connection process|Initiator status|Acceptor status|
|:-----------------|:---------------|:--------------|
|The initiator initiates a connection.|Connecting|Accepting|
|The connection is established.|Activated|Activated|
|The connection is suspended.|Suspending|Suspending|
|The connection is broken.|Suspended|Suspended|
|A connection is re-initiated.|Activating|Activating|
|The connection is established.|Activated|Activated|

