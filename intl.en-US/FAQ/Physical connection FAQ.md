# Physical connection FAQ {#concept_gpt_1qb_12b .concept}

## Does a physical connection enable an on-premises IDC connected to Alibaba Cloud to access different regions? {#section_hqs_bqb_12b .section}

Yes. The on-premises IDC can access VPCs in all regions of Alibaba Cloud after the physical connection is established.

## What types of physical connections does Alibaba Cloud support? {#section_iqs_bqb_12b .section}

Alibaba Cloud devices support Ethernet optical interfaces and electrical interfaces. For optical interfaces, 10GE and Gigabit single-mode LC optical modules are provided by default at a distance of 10 km. Modules of other specifications require two to four weeks' preparations \(such as 10GE multi-mode LC modules and Gigabit multi-mode LC modules at a distance of 10 km\). If you require modules to be positioned at a distance other than 10 km, you need to manually prepare the module before providing it to Alibaba Cloud.

## What is the maximum bandwidth of a physical connection? {#section_jqs_bqb_12b .section}

The highest port specification available in the console is 10G. If you need a higher value, open a ticket to apply for it.

## Does a physical connection support dynamic routing protocols? {#section_kqs_bqb_12b .section}

Physical connection supports using the BGP dynamic routing protocol to forward data between the on-premises IDC and the VPC.

## Is disaster tolerance of multiple physical connections supported? {#section_lqs_bqb_12b .section}

ECMP implemented by up to four physical connections is supported.

## Can I use a physical connection to connect multiple VPCs? {#section_nqs_bqb_12b .section}

Yes. The new VPC reuses the existing VBR. You only need to create a new router interface to connect the new VPC to the VBR.

## How many VPCs can a physical connection connect at most? {#section_oqs_bqb_12b .section}

Up to five routers can be created for one physical connection and up to 10 peering connections can be established for each VBR.

## Can I extend my local VLAN to a VPC through physical connection? {#section_pqs_bqb_12b .section}

No. Currently, Alibaba Cloud only supports Layer-3 interconnection.

## If a physical connection is connected to multiple VPCs, are the networks of the VPCs over the physical connection isolated from one another? {#section_qqs_bqb_12b .section}

You can isolate network data by dividing VLANs on the physical connection. For more information, see [Create a virtual border router](../../../../../intl.en-US/User Guide (New Console)/Virtual border router/Create a virtual border router.md#).

## Does physical connection support NAT? {#section_rqs_bqb_12b .section}

Physical Connection does not support configuring NAT now. If you must use NAT in special scenarios, you need to configure NAT in your on-premises IDC.

## What is the relation between zones and access points? {#section_sqs_bqb_12b .section}

Both zones and access points belong to a region. Any access point in a region can use all zones in this region.

If an access point and a VPC are in different regions, you can use a cross-region Express Connect to connect them.

## My cloud server is in zone A, which access point should I use to connect to zone A? {#section_vqs_bqb_12b .section}

Both zones and access points are located in regions, but they are not mapped in a one-to-one relationship. Specifically, access points are deployed at Alibaba Cloud AP locations \(that is, sites where the network service is provided\). As a result, in some regions, an AP location can be in the same geographic position as that of a zone.

## What is the process of establishing a physical connection? {#section_yqs_bqb_12b .section}

To establish a physical connection, follow these steps:

1.  Determine an appropriate access point.
2.  Apply for a physical connection interface and pay the initial installation fee.
3.  Apply for the LOA and begin installation work for the physical connection.
4.  Contact Alibaba Cloud to complete the installation and pay the resource fee.
5.  Enable the physical connection interface.
6.  Configure a VBR.
7.  Add the VBR to the CEN, or create a VBR-to-VPC peering connection.
8.  Configure routes and test the connectivity between hosts \(generally, the physical connection is normal if a ping test succeeds\).

## What factors need to be considered before establishing a physical connection to a VPC? {#section_zqs_bqb_12b .section}

-   Whether only one physical connection is required, or multiple physical connections are required to achieve load balancing or highly reliable redundancy.

-   Determine a suitable bandwidth. Generally, a selection of 10 Mbit/s, 100 Mbit/s, 1 Gbit/s, or 10 Gbit/s meets most requirements.

-   Determine the interface type of the physical connection. Available interfaces include optical interfaces and electrical interfaces. If you use optical interfaces, the compatibility between the optical modules \(including factors such as distance, device brand, and more\) must be considered.

-   Demands for Alibaba Cloud's other cloud services and the expected VPC scale. \(When a VPC is created, the CIDR Block of the VPC can be determined based on the expected VPC scale.\)


## How do I plan IP addresses for physical connection access? {#section_brs_bqb_12b .section}

IP addresses at the two ends of the physical connection cannot conflict with each other and must be private IP addresses. If the customer side is using a public IP address, open a ticket to configure a private IP address.

## What is the VLAN ID of the VBR? {#section_crs_bqb_12b .section}

-   When the VLAN ID is 0, physical switch ports of the VBR use the Layer-3 router interface mode instead of the VLAN mode. In the Layer-3 router interface mode, each leased line corresponds to a VBR, which means that a leased line can only be connected to VPCs under the same account.

-   When the VLAN ID is \[1, 2999\], the physical switch ports of the VBR use VLAN-based Layer-3 subinterfaces. In the Layer-3 subinterface mode, each VLAN ID corresponds to a VBR, which means that a leased line can be connected to VPCs under different accounts.


Assume a company includes multiple departments or subsidiaries. Each of the departments or subsidiaries has an independent Alibaba Cloud account and each account includes a VPC. When applying for a leased line, the company needs to plan VLAN IDs for each department or subsidiary. When creating a VBR, the company uses VLAN IDs to identify departments or subsidiaries.

## What do the Alibaba Cloud-side IP address and customer-side IP address in a VBR mean? {#section_ers_bqb_12b .section}

The Alibaba Cloud-side IP address is the IP address used as the gateway to connect to the on-premises IDC. The customer-side IP address is the IP address used as the gateway to connect to VPC. You must plan an IP address for each side of the leased line to connect the on-premises IDC to the VPC. The two IP addresses must be in the same CIDR block.

## How to verify that the leased line connection is completed? {#section_grs_bqb_12b .section}

After the installation is completed at the service provider side, Alibaba Cloud will change the leased line status to **Waiting**. To complete the leased line connection, you must log on to the Express Connect console, choose **Physical Connections** \> **Physical Connection Interfaces** in the left-side navigation pane, and click **Confirm**. If the leased line status changes to **Enabled**, the leased line connection is completed. After that, you need to create a VBR and configure routes to complete the physical connection. For more information, see [Connect an on-premises IDC to a VPC through a physical connection](../../../../../intl.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).

## How does the on-premises IDC access the OSS intranet domain name in the VPC? {#section_hrs_bqb_12b .section}

The OSS intranet domain name belongs to 100.64.0.0/10, which is a CIDR block reserved by Alibaba Cloud. Therefore, a route pointing to 100.64.0.0/10 cannot be directly added to the VBR. If you have related demands, split 100.64.0.0/10 into smaller subnets, for example, 100.64.0.0/11 and 100.96.0.0/11. Add them to the route table of the VBR, and set the next hop direction to VPC.

## The communication line to Alibaba Cloud is disconnected, what should I do? {#section_jrs_bqb_12b .section}

Test whether the client-side IP address can successfully ping the Alibaba Cloud-side IP address on the gateway device of the on-premises IDC. If the ping test fails, report the fault to the service provider. A physical switch port on the Alibaba Cloud side connects the VPC to the on-premises IDC. If the port is blocked, the leased line of the service provider is interrupted. In this case, report the fault to the service provider.

## What should I do if the bandwidth does not meet the expectation? {#section_krs_bqb_12b .section}

If the router interface speed is lower than 1 Gbit/s, use iPerf to test the bandwidth. If the bandwidth cannot exceed 10 Mbps, it is possible that ports at one end of the leased line run in half duplex mode after negotiation. You can request the carrier to change the port mode to adaptive mode.

If the router interface speed exceeds 1 Gbps, the speed of each data stream is limited to a certain degree \(130 Mbps or 250 Mbps\) because the data streams use different loading mode.

## What should I do if an error is returned when I add or delete a route entry on the VBR? {#section_lrs_bqb_12b .section}

Because the hardware of the VBR is slow in processing, before you add or delete a route entry, wait until the processing of the last route is completed.

## What can I do if a token error is returned when I add a route entry? {#section_mrs_bqb_12b .section}

This error is caused by cookie timeout of your browser. Log out of your account and log on again.

