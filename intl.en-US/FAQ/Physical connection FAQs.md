# Physical connection FAQs {#concept_gpt_1qb_12b .concept}

## Does a physical connection enable a local data center connected to Alibaba Cloud to access different regions? {#section_hqs_bqb_12b .section}

Yes. The local data center can access VPCs in all regions of Alibaba Cloud after the physical connection is established.

## What types of physical connections does Alibaba Cloud support? {#section_iqs_bqb_12b .section}

Alibaba Cloud devices support Ethernet optical interfaces and electrical interfaces. For optical interfaces, 10-km 10-GE single-mode LC optical modules are provided by default. Modules of other specifications are provided within two to four weeks, such as 10-km 10-GE multi-mode LC module, 10-km gigabit single-mode LC module and 10-km gigabit multi-mode LC module. You must prepare all other modules by yourself, and Alibaba Cloud will keep them for you.

## What is the maximum bandwidth of a physical connection? {#section_jqs_bqb_12b .section}

For a physical connection, Alibaba Cloud supports up to 10 Gbit/s bandwidth.

## Does a physical connection support dynamic routing protocols? {#section_kqs_bqb_12b .section}

Physical connection supports using the BGP dynamic routing protocol to forward data between the local data center and the VPC.

## Is disaster tolerance of multiple physical connections supported? {#section_lqs_bqb_12b .section}

ECMP implemented by up to four physical connections is supported.

## Can I use a physical connection to connect multiple VPCs? {#section_nqs_bqb_12b .section}

Yes. The new VPC reuses the existing VBR. You only need to create a new router interface to connect the new VPC to the VBR.

## How many VPCs can a physical connection connect at most? {#section_oqs_bqb_12b .section}

Each VRouter instance supports six router interfaces by default. When Layer-3 router interfaces are used for interconnection, a maximum of five VPCs can be connected at the same time.

## Can I extend my local VLAN to a VPC through physical connection? {#section_pqs_bqb_12b .section}

No. Currently, Alibaba Cloud only supports Layer-3 interconnection.

## If a physical connection is connected to multiple VPCs, are the networks of the VPCs over the physical connection isolated from one another? {#section_qqs_bqb_12b .section}

You can isolate network data by dividing VLANs on the physical connection. For more information, see [Create a virtual border router](../../../../reseller.en-US/User Guide (New Console)/Virtual border router/Create a virtual border router.md#).

## Does physical connection support NAT? {#section_rqs_bqb_12b .section}

Physical Connection does not support configuring NAT now. If you must use NAT in special scenarios, you need to configure NAT in your local data center.

## What is the relation between zones and access points? {#section_sqs_bqb_12b .section}

Both zones and access points belong to a region. Any access point in a region can use all zones in this region.

If an access point and a VPC are in different regions, you can use a cross-region Express Connect to connect them.

## What are the limits on the service providers of Alibaba Cloud access points? {#section_tqs_bqb_12b .section}

For more information about access points, open a ticket.

|Region|Access point|Supported service provider|
|:-----|:-----------|:-------------------------|
|Beijing|Changping A|China Telecom|
|Daxing B|China Unicom|
|Shanghai|Baoshan A|China Telecom|
|Baoshan B|China Unicom|
|Pudong A|China Telecom|
|Pudong B|China Telecom|
|Shenzhen|Hualong A|China Telecom|

## My cloud server is in zone A, which access point should I use to connect to zone A? {#section_vqs_bqb_12b .section}

Both zones and access points are in regions and there is no strict correlation between them. Access points are deployed at Alibaba POPs in a region. A POP and a zone can be at the same geographic location in some regions.

## How is physical connection access charged? {#section_wqs_bqb_12b .section}

## How can I achieve Express Connect connection with a VPC outside China? {#section_xqs_bqb_12b .section}

To establish cross-border Express Connect, you must submit a **commitment letter**. You can contact your customer manager to obtain the commitment letter.

## What is the process of physical connection access? {#section_yqs_bqb_12b .section}

Apply for a leased line \> pay for the initial installation fee and obtain the access point location \> negotiate with the carrier and sign a contract \> the carrier assigns engineers to connect the two sides \> configure the VBR \> create router interfaces \> configure routes \> test the connectivity from hosts on the two sides \(Generally, if the ping test is successful, the connection is normal\) \> the physical connection is successfully established.

## What factors need to be considered before establishing a physical connection to VPC? {#section_zqs_bqb_12b .section}

-   Whether only one physical connection is required, or multiple physical connections are required to achieve load balancing or highly reliable redundancy.

-   Bandwidth. Generally, the bandwidth is 10 Mbps, 100 Mbps, 1 Gbps, or 10 Gbps. The carrier will provide detailed specifications.

-   Interface type of physical connection. Available interfaces include optical interfaces and electrical interfaces. Generally, we recommend that you use electrical interfaces \(RJ45 interface\). If you use optical interfaces, the compatibility \(of distance, device brand, and so on\) between the optical modules on the two sides needs to be considered.

-   Demands for Alibaba Cloud's other cloud services and the expected VPC scale. \(When a VPC is created, the CIDR Block of the VPC can be determined based on the expected VPC scale.\)


## How do I plan IP addresses for physical connection access? {#section_brs_bqb_12b .section}

IP addresses at the two ends of the physical connection cannot conflict with each other and must be private IP addresses. If the customer side is using a public IP address, open a ticket to configure a private IP address.

## What is the VLAN ID of the VBR? {#section_crs_bqb_12b .section}

-   When the VLAN ID is 0, physical switch ports of the VBR use the Layer-3 router interface mode instead of the VLAN mode. In the Layer-3 router interface mode, each leased line corresponds to a VBR, which means that a leased line can only be connected to VPCs under the same account.

-   When the VLAN ID is \[1, 2999\], the physical switch ports of the VBR use VLAN-based Layer-3 subinterfaces. In the Layer-3 subinterface mode, each VLAN ID corresponds to a VBR, which means that a leased line can be connected to VPCs under different accounts.


Assume a company includes multiple departments or subsidiaries. Each of the departments or subsidiaries has an independent Alibaba Cloud account and each account includes a VPC. When applying for a leased line, the company needs to plan VLAN IDs for each department or subsidiary. When creating a VBR, the company uses VLAN IDs to identify departments or subsidiaries.

## What do the Alibaba Cloud-side IP address and customer-side IP address in a VBR mean? {#section_ers_bqb_12b .section}

The Alibaba Cloud-side IP address is the IP address used as the gateway to connect to the local data center. The customer-side IP address is the IP address used as the gateway to connect to VPC. You must plan an IP address for each side of the leased line to connect the local data center to the VPC. The two IP addresses must be in the same CIDR block.

## How do I arrange for on-site leased line construction by the service provider? {#section_frs_bqb_12b .section}

If you have paid for the leased line, log on to the Express Connect console and click **Physical Connection \> Leased Line** in the left-side navigation pane. You can see the ID of the applied leased line. Then click **View** on the right side to view information about leased line construction, such as data center location, network cabinet location, and port information. Inform your service provider of the port information and ask the service provider to connect the leased line.

After completing survey, the service provider will provide you a file containing names of personnel dispatched to the data center of the access point and related information, time of on-site construction, leased line ID and so on. At this time, you need to open a ticket to inform Alibaba Cloud aftersales personnel of information about leased line laying by construction personnel of the service provider.

## How to verify that the leased line access is completed? {#section_grs_bqb_12b .section}

After the construction is completed, after sales personnel of Alibaba Cloud changes the leased line status to **Awaiting Confirmation**. Log on to the Express Connect console, click **Physical Connection \> Leased Line** in the left-side navigation pane, and click **Confirm**. If the leased line status changes to **Normal**, the leased line access is completed. Then you need to create a VBR and configure routes to achieve leased line communication. For more information, see [Connect a local IDC to a VPC through a physical connection](../../../../reseller.en-US/Getting Started (New Console)/Connect a local IDC to a VPC through a physical connection.md#).

## How does the local data center access the OSS intranet domain name in the VPC? {#section_hrs_bqb_12b .section}

The OSS intranet domain name belongs to 100.64.0.0/10, which is a CIDR block reserved by Alibaba Cloud. Therefore, a route pointing to 100.64.0.0/10 cannot be directly added to the VBR. If you have related demands, split 100.64.0.0/10 into smaller subnets, for example, 100.64.0.0/11 and 100.96.0.0/11. Add them to the route table of the VBR, and set the next hop direction to VPC.

## I submitted a leased line application some time ago but why is the status still “Application in progress”? {#section_irs_bqb_12b .section}

After you submit the physical connection application, the leased line status changes to **Applying**. Then, the personnel of Alibaba Cloud will contact you within two workdays to verify your application. After your application is approved, the leased line status changes to **Approved**.

## The communication line to Alibaba Cloud is disconnected, what should I do? {#section_jrs_bqb_12b .section}

Test whether the client-side IP address can successfully ping the Alibaba Cloud-side IP address on the gateway device of the local data center. If the ping test fails, report the fault to the service provider. A physical switch port on the Alibaba Cloud side connects the VPC to the local data center. If the port is blocked, the leased line of the service provider is interrupted. In this case, report the fault to the service provider.

## What should I do if the bandwidth does not meet the expectation? {#section_krs_bqb_12b .section}

If the router interface speed is lower than 1 Gbit/s, use iPerf to test the bandwidth. If the bandwidth cannot exceed 10 Mbps, it is possible that ports at one end of the leased line run in half duplex mode after negotiation. You can request the carrier to change the port mode to adaptive mode.

If the router interface speed exceeds 1 Gbps, the speed of each data stream is limited to a certain degree \(130 Mbps or 250 Mbps\) because the data streams use different loading mode.

## What should I do if an error is returned when I add or delete a route entry on the VBR? {#section_lrs_bqb_12b .section}

Because the hardware of the VBR is slow in processing, before you add or delete a route entry, wait until the processing of the last route is completed.

## What can I do if a token error is returned when I add a route entry? {#section_mrs_bqb_12b .section}

This error is caused by cookie timeout of your browser. Log out of your account and log on again.

