# Implement redundancy for physical connections {#task_1545758 .task}

To make sure that traffic is forwarded to the standby physical connection when the active physical connection fails, you must configure health checks for the associated VBR-to-VPC peering connections and configure route weights.

Before you configure health checks and route weights, make sure that the following operations are completed:

-   Two physical connection interfaces are applied for and the connection between the on-premises data center and Alibaba Cloud is established.
-   Two VBR-to-VPC peering connections are created. For more information, see [Apply for a physical connection interface](../reseller.en-US/Physical Connection/Apply for a physical connection interface.md#) and [Interconnect a VPC and a VBR](../reseller.en-US/Peering connections/Interconnect a VPC and a VBR.md#).
-   Static routes are configured between the Virtual Border Routers \(VBRs\) and the on-premises data center. No BGP is used.

Alibaba Cloud sends a ping packet once every two seconds from the health check IP address to the customer-side IP address of the on-premises data center. If no response is received for the ping packet for eight consecutive times on one physical connection, traffic is switched to the other physical connection.

**Note:** If Control Plane Policing \(Copp\) \(such as Cisco devices\) or Local Attack Defense Policy \(Huawei devices\) is configured on the on-premises data center, health check packets may be discarded and the health check link shocks. Therefore, we recommend that you cancel the speed limitation on the network device of the on-premises data center.

![Access VPC from an on-premises data center](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981154306_en-US.png)

The network configurations are as follows:

|Configuration|CIDR block|
|-------------|----------|
|The connected VPC|192.168.0.0/16|
|The on-premises data center|172.16.0.0/16|
|The connection between one VBR and the on-premises data center| -   VBR gateway IP address: 10.10.10.1
-   Gateway IP address of the on-premises data center: 10.10.10.2
-   Subnet mask: 255.255.255.252

 |
|The connection between the other VBR and the on-premises data center| -   VBR gateway IP address: 10.10.11.1
-   Gateway IP address of the on-premises data center: 10.10.11.2
-   Subnet mask: 255.255.255.252

 |
|Health checks for one VBR-to-VPC peering connection| -   Source IP address: 192.168.10.1
-   Destination IP address: 10.10.10.2

 |
|Health checks for the other VBR-to-VPC peering connection| -   Source IP address: 192.168.10.2
-   Destination IP address: 10.10.11.2

 |

## Step 1 Configure health checks {#section_02h_835_9ny .section}

You must configure health checks for the two peering connections. To do so, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Find the target peering connection and choose **![More](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981154309_en-US.png)** \> **Health Check** in the **Actions** column.
4.  On the Health Check page, click **Configure**.
5.  On the Edit VBR page, configure health checks. The following table shows the required parameters.

    |Parameter|Description|
    |---------|-----------|
    |Source IP|Any idle private IP address in the connected VPC.|
    |Destination IP|The interface IP address of the network device of the on-premises data center. If you need to perform ICMP health checks from the on-premises data center to the VPC, enter the health check IP address of the VPC as the destination IP address and configure a route that points to the new health check destination.

 |

    ![Health checks](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981154391_en-US.png)

6.  Click **OK**.
7.  Repeat the preceding steps to configure health checks for the other peering connection. 

    **Note:** The source IP address of the health check for the other peering connection cannot be the same as that for the first peering connection.


## Step 2 Configure routes {#section_6u8_1u6_bt1 .section}

In this example, load balancing routing is configured.

1.  In the left-side navigation pane, choose **Route Tables**.
2.  Find the target VPC and click the ID of the corresponding route table.
3.  On the Route Table page, click **Add Route Entry** and configure the load balancing route. Configure the load balancing route according to the following information:

    -   **Destination CIDR Block**: Enter the destination CIDR block to which traffic is forwarded.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**, which means forwarding the traffic with a destination IP address that falls into the destination CIDR block to the router interface associated with the VBR.

        Select **Load Balancing Routing** for the routing type, select the two VBRs connected with the VPC as the next hop, and set weights for the two VBRs. Value range of the weights of the VBRs: 1 to 255. Default value: 100. The weights of the two VBRs must be the same so that traffic can be evenly distributed to them.

    ![Configure load balancing route](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981154353_en-US.png)

4.  Click **Add Route Entry** and add a route from one VBR to the on-premises data center. Configure the route according to the following information:
    -   **Destination CIDR Block**: Enter the destination CIDR block.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**, which means forwarding the traffic with a destination IP address that falls into the destination CIDR block to the router interface associated with the VBR.

        Select **General Routing** for the routing type and select one VBR as the next hop.

5.  Click **Add Route Entry** and configure a route from the other VBR to the on-premises data center. Configure the route according to the following information:

    -   **Destination CIDR Block**: Enter the destination CIDR block.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**, which means forwarding the traffic with a destination IP address that falls into the destination CIDR block to the router interface associated with the VBR.

        Select **General Routing** for the routing type and select the other VBR as the next hop.

    The following figure shows the configured routes.

    ![Route entry](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981154373_en-US.png)


## Step 3 Configure static routes on the network device of the on-premises data center {#section_i3z_mp0_y5r .section}

If no BGP is used, the following static routes need to be configured for between the on-premises data center and the VBRs on the network device of the on-premises data center:

-   A route entry with the health check source IP address of one peering connection as the destination IP address and the IP address of the corresponding VBR \(Alibaba Cloud-side IP address\) as the next hop.
-   A route entry with the health check source IP address of the other peering connection as the destination IP address and the IP address of the corresponding VBR as the next hop.

## Step 6 Test the network connectivity {#section_ghk_iuc_q03 .section}

Ping an instance in the VPC when one physical connection fails to check if the redundant physical connection works.

## Advertise BGP CIDR blocks {#section_vgs_btq_xvq .section}

If you have configured BGP for your on-premises data center and the VBRs, the VBRs need to advertise BGP CIDR blocks.

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Find one of the two VBRs and click the VBR ID. On the Routes tab, click **Add Route**.
4.  On the Add Route page, configure a route pointing to the health check source IP address. Configure the route according to the following information:

    -   **Destination Subnet**: Enter the source IP address of health checks. In this example, enter 192.168.10.1/32.
    -   **Next Hop Type**: Select **VPC**. Then, select the connected VPC as the next hop.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981254421_en-US.png)

5.  Click the Advertised BGP Subnets tab and click **Advertise BGP Subnet**.
6.  On the Advertise BGP Subnet page, enter the source IP address of health checks. 

    ![Advertise BGP CIDR block](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1227037/156558981254424_en-US.png)

7.  Repeat the preceding steps to advertise BGP CIDR blocks for the health check source IP address of the other VBR.

