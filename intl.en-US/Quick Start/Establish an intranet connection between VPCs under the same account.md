# Establish an intranet connection between VPCs under the same account {#concept_wrx_vbr_ydb .concept}

This tutorial illustrates how to use Express Connect to connect two VPCs under the same account.

## Example {#section_ock_bcr_ydb .section}

This tutorial takes the following two VPCs as an example to show how to achieve VPC intranet interconnection by using Express Connect.

|Configuration|VPC1|VPC2|
|:------------|:---|:---|
|VPC ID|vpc-12345678|vpc-12345678|
|Region|China \(Beijing\)|China \(Hangzhou\)|
|VPC CIDR block|192.168.0.0/16|172.16.0.0/12|
|VSwitch CIDR block|192.168.100.0/24|172.16.100.0/24|

## Prerequisites {#section_kdw_xbr_ydb .section}

Make sure that the CIDR blocks of the VPCs or VSwitches to be interconnected do not conflict with each other.

## Step 1: Create router interfaces {#section_ldw_xbr_ydb .section}

Follow these steps to create router interfaces:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-beijing/list).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **Create Router Interface**.
4.  Configure the router interface and complete the payment.

    This tutorial uses the following configurations.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Router Creation**: Select **Create Initiator and Receiver**. The system sets the router interface of the local side as the initiator, and automatically connects the initiator to the receiver.

    -   **Local Region**: Select the region where the VPC is located. In this tutorial, select **China \(Beijing\)**.

    -   **VPC ID**: Select the VPC to be connected. In this tutorial, select **VPC1**.

    -   **Peer Region**: Select the region where the peer VPC is located. In this tutorial, select **China \(Hangzhou\)**.

    -   **Peer VPC ID**: Select the peer VPC to be connected. In this tutorial, select **VPC2**.

    -   **Specification**: Select the specification of the initiator router interface. In this tutorial, select **Large.1**.


After the router interfaces are created, the system automatically initiates the connection between the router interfaces as shown in the following figure:

-   Initiator router interface

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21767/153813796712716_en-US.png)

-   Receiver router interface

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21767/153813796712717_en-US.png)


## Step 2: Configure the routes {#section_tdw_xbr_ydb .section}

After creating the router interfaces, follow these steps to configure routes for the two VPCs:

1.  On the Router Interface page, find the target router interface and click **Router Configuration**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21767/153813796712718_en-US.png)

2.  On the Route Table page, click **Add Route Entry**.
3.  In the displayed dialog box, configure the route according to the following information:
    -   **Destination CIDR Block**: The CIDR block of the peer VPC or VSwitch.
    -   **Next Hop Type**: Select **Router Interface**.
    -   **Router Interface**: Select **General Routing** and select a router interface.
4.  Repeat the preceding steps to configure the route for the VPC associated with the peer router interface.

    In this tutorial, the router configurations are as follows:

    |Destination CIDR block|Next Hop|Description|
    |:---------------------|:-------|:----------|
    |172.16.100.0/24 \(VSwitch CIDR block of VPC2\)|Router interface of VPC1|Route table configuration of VPC1|
    |192.168.100.0/24 \(VSwitch CIDR block of VPC1\)|Router interface of VPC2|Route table configuration of VPC2|


## Step 3: Configure security groups {#section_zx1_ndf_hfb .section}

After establishing a peer connection between two VPCs, you can configure security group rules to make the ECS instances in the connected VPCs communicate with each other.

This tutorial uses ECS instances and security group configurations in the following table as an example.

|Configurations|Account A|Account A|
|:-------------|:--------|:--------|
|Account ID|AccountID\_A|AccountID\_A|
|ECS instance ID|InstanceID\_A|InstanceID\_B|
|Security group ID|SecurityGroupID\_A|SecurityGroupID\_B|

You can view the account ID in the [Account Center](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21767/153813796713076_en-US.png)

To configure security groups, complete these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Networks and Security** \> **Security Groups**.
3.  Select a region.
4.  Find the target security group and then click **Add Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rule**.
6.  Configure the security group rule, select the protocol type and enter the port range. Note the following configurations:

    -   **Authorization Type**: Select **Security Group** and then select **Allow Other Accounts**.
    -   **Authorization Objects**: Enter the security group ID associated with the ECS instance to be accessed by other ECS instances.
    -   **Account ID**: Enter the ID of your account.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21767/153813796813077_en-US.png)


