# Router interfaces {#concept_ymg_rry_xdb .concept}

A router interface is a virtual device with the ability to set up a communication channel and control its working status.

Express Connect builds an intranet communication channel between two VPCs by creating two router interfaces individually for the VRouters of the VPCs. The VRouters can send messages to each other through the channel after the connection between the two router interfaces is established. Therefore, the resources in the two VPCs \(such as ECS instances\) can communicate over the intranet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13811/15382983554200_en-US.jpg)

## Initiator and receiver {#section_lcr_v4q_ydb .section}

When two router interfaces are interconnecting, one plays the role of the connection initiator and the other plays the role of the connection receiver. Only the initiator router interface can initiate a connection; the receiver router interface must wait for the initiator to start a connection. The initiator and receiver are only used to control the process of establishing connections. In the actual network communication, the communication link is bidirectional and there is no difference between the initiator and receiver.

For the VPC interconnection of a same account, Express Connect provides an option to create two router interfaces at the same time. In this situation, you do not need to manually initiate the connection, the system automatically initiates and establishes the connection. For the VPC interconnection of different accounts, you have to manually initiate a connection between the initiator router interface and the receiver router interface.

The following table is the comparison between the initiators and receivers.

|Items| Initiator router interfaces|Receiver router interfaces|
|:----|:---------------------------|:-------------------------|
|Is the interface charged when connecting two VPCs in the different regions?|Yes|No|
|Is configuring peer router interface information required before initiating a connection?|Yes|No|
|Is configuring peer router interface information required before initiating a connection?|Yes|Yes|
|Can the interface initiate a connection?|Yes|No|
|Can the interface send messages to the peer interface after the connection is established?|Yes|Yes|
|Can the role of router interfaces be modified after the router interfaces are created?|No|No|

## Connection process {#section_qcr_v4q_ydb .section}

An initiator router interface initiates a connection. Then, the receiver router interface accepts the connection. At last, establish the connection.

In different connection process and stage, the status of router interface is also different as shown in the following table.  The initial state of the router interface after it is created is Not connected.

**Note:** If you select create the initiator and receiver router interfaces at the same time, the system automatically initiates and establishes a connection. In this situation, the status of the router interfaces directly change to Activated.

|Connection process|Initiator router interface|Receiver router interface|
|:-----------------|:-------------------------|:------------------------|
|An initiator router interface initiates a connection|Connecting| Accepting connection|
|Connection is established|Activated|Activated|
|Freeze a connection|Freezing|Freezing|
|Connection is disconnected|Frozen|Frozen|
|Activate a frozen connection|Activating|Activating|
|Connection is established|Activated|Activated|

## Router interface specification {#section_wcr_v4q_ydb .section}

Express Connect provides three kinds of interface specifications: small \(10 Mbps-50 Mbps\), middle \(100 Mbps-900 Mbps\), and large \(1 Gbps-4.5 Gbps\).

The available router interface specifications are different in different connection scenarios and regions. Select an appropriate specification according to your configurations on the purchase page. The router interface specification used for same-region VPC interconnection is set to Large 2 \(2 Gbps\) by default.

The available specifications are as follows.

|Specifications |Capacity|
|:--------------|:-------|
|Small|Small 1=10, Small. 2=20, Small. 5=50|
|Medium|Middle. 1=100, Middle. 2=200, Middle. 5=500, Middle. 7=700, Middle. 4=400, Middle. 6=600, Middle. 7=700, Middle. 8=800, Middle. 9=900|
|Large|Large. 1=1000, Large. 1.1=1100, Large. 1.2=1200, Large. 1.3=1300, Large. 1.4=1400, Large. 1.5=1500, Large. 1.6=1600, Large. 1.7=1700, Large. 1.8=1800, Large. 1.9=1900, Large. 2=2000, Large. 2.5=2500, Large. 3=3000, Large. 3.5=3500, Large. 4=4000, Large. 4.5=4500, Large. 5=5000, Xlarge. 1=10000, Xlarge. 4=40000, Xlarge. 8=80000, Xlarge. 10=100000|

## Limits {#section_ohj_jtq_ydb .section}

-   Only one pair of router interface connection is allowed between two VPCs.

-   The connection role of a router interface cannot be modified after the router interface is created.

-   Virtual border routers \(VBRs\) always act as the connection initiator.


