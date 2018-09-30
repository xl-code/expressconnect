# Create a virtual border router {#concept_ihj_w11_ydb .concept}

## What is Virtual Border Router? {#section_kpn_db1_ydb .section}

Virtual Border Router \(VBR\) is the mapping of your leased line in VPC. It can be regarded as a VRouter between Customer Premise Equipment \(CPE\) and VPC, and acts as the forwarding bridge between a local data center and a VPC.

VBR includes a route table. You can manage traffic forwarding in VBR through configuring route entries in VBR. VBR provides the following functions:

-   Exchange data packets as the intermediate VRouter between VPC and the local data center.
-   Decide the interface mode of the leased line: Layer-3 router interface mode or VLAN-based layer-3 subinterface mode.
-   Recognize or attach VLAN tags in layer-3 subinterface mode.
-   Support BGP dynamic routing.

## Limits { .section}

-   Each route table supports up to 48 custom route entries.
-   Source address based policy routing is not supported.

## Procedure { .section}

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
3.  In the upper-right corner, click **Create VBR**. Configure the VBR according to the following information and click **Confirm Creation**.

    |Configuration|Description|
    |:------------|:----------|
    |**Object**|     -   If you want to create a VBR for the leased line under another account, select **Other Account**.
    -   If you want to create a VBR for the leased line under this account, select **This Account**.
 |
    |**Name**|Enter the name of the VBR.|
    |**Description**|Enter the description of the VBR.|
    |**Leased Line**|Select the leased line to be connected to the VBR.|
    |**VLAN ID**|Enter the VLAN ID of the VBR, in the range of 0-2999.    -   VLAN When the VLAN ID is 0, the physical switch port of the VBR uses the layer-3 router interface mode instead of the VLAN mode. In the layer-3 router interface mode, each leased line corresponds to a VBR.
    -   When the VLAN ID is \[1-2999\], the physical switch port of the VBR uses the VLAN-based layer-3 subinterface mode. In the layer-3 subinterface mode, each VLAN ID corresponds to a VBR. In this mode, the leased line of the VBR can connect VPCs under multiple accounts. VBRs of different VLANs are isolated from one another.

For example, a company has multiple subdivisions or subsidiaries. Each subdivision or subsidiary has an independent Alibaba Cloud account, and each account has an independent VPC.  If the company applies for a leased line, it needs to plan a VLAN ID for each subdivision or subsidiary. When creating router interfaces, the company uses VLAN IDs to identify the subsidiaries or subdivisions to use the leased line.

|
    |**Circuit Code**|The carrier that builds the leased line for you will provide a circuit code for your leased line. Enter the circuit code to facilitate maintenance.|
    |**IP Address**|     -   **Alibaba Cloud-Side**: Enter the IP address used as the gateway to connect to the local data center.
    -   **Customer-Side**: Enter the IP address used as the gateway to connect to VPC.
    -   **Subnet Mask**: The subnet mask of the Alibaba Cloud-side IP address and the customer-side IP address. Because only two IP addresses are required, you can enter a long subnet mask.
 |


