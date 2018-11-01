# Peering connection {#concept_ymg_rry_xdb .concept}

You can establish a peering connection between two VPCs or between a VPC and a VBR.

## Initiator and acceptor {#section_lcr_v4q_ydb .section}

When you establish a peering connection, one end \(VPC or VBR\) of the connection is the initiator, and the other end is the acceptor. Only the initiator can initiate a connection. The acceptor can only wait for the initiator to initiate a connection. The initiator and acceptor are only used to control the connection-establishing process. In network communication, the communication link is bidirectional and there is no difference between the initiator and acceptor.

For VPC interconnection under the same account, Express Connect provides an option to create the initiator and acceptor at the same time. In this case, you do not need to manually initiate a connection. The system automatically initiates and establishes a connection. For VPC interconnection under different accounts, you need to manually initiate a connection.

The following table compares the initiator with the acceptor.

|Item|Initiator|Acceptor|
|:---|:--------|:-------|
|Is the end charged when two VPCs are interconnected in the same region?|No.|No.|
|Is the end charged when two VPCs are interconnected between two different regions?|Yes.|No.|
|Is configuring peer information required before initiating a connection?|Yes.|Yes.|
|Can the end initiate a connection?|Yes.|No.|
|Can the end send messages to the peer end after a connection is established?|Yes.|Yes.|

## Connection process and status {#section_qcr_v4q_ydb .section}

In a peering connection process, the initiator initiates a connection, and then the acceptor receives the connection until the connection succeeds.

In different connection processes and stages, the statuses of a peering connection are also different, as shown in the following table.

**Note:** If you choose to create both ends at the same time when establishing a peering connection, the system automatically initiates and establishes a connection. In this case, the initiator and acceptor become activated after being created.

|Connection process|Initiator status|Acceptor status|
|:-----------------|:---------------|:--------------|
|The initiator initiates a connection.|Connecting|Accepting the connection|
|The connection is established.|Activated|Activated|
|The connection is suspended.|Suspending|Suspending|
|The connection is broken.|Suspended|Suspended|
|A connection is re-initiated.|Activating|Activating|
|The connection is established.|Activated|Activated|

