# VPC-to-VPC connection FAQ {#concept_h5w_vpb_12b .concept}

## Does the data transferred through Express Connect go over the Internet? {#section_vd1_ypb_12b .section}

No. Data on Express Connect is transmitted only inside Alibaba Cloud data centers or over lease lines among the data centers and does not pass through the Internet. This avoids data leakage during transmission and provides better network quality than the Internet.

## Does Express Connect support cross-account VPC-to-VPC connections? {#section_wd1_ypb_12b .section}

Yes. Express Connect supports intranet connections between two VPCs under the same account or different accounts. For more information, see [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13830.md\#](../../../../reseller.en-US/Peering connections/Interconnect two VPCs under the same account.md#).

## Does Express Connect support cross-region VPC-to-VPC connections? {#section_xd1_ypb_12b .section}

Yes. Express Connect supports intranet connections between VPCs in the same region or different regions. You can create a router interface on the VRouter of each VPC respectively and build Express Connect through Alibaba Cloud's backbone transmission network to achieve secure, reliable, fast, and convenient communication between the VPCs.

## After I connect two VPCs by using Express Connect, what resources of one VPC can the other VPC access? {#section_yd1_ypb_12b .section}

ECS instances of either VPC can access the ECS instances, Server Load Balancer \(SLB\) instances, and RDS instances of the other VPC.

-   However, the SLB instances of either VPC cannot use ECS instances of the other VPC as backend servers.
-   Currently, cloud product instances other than ECS instances, SLB instances, and RDS instances of either VPC cannot be accessed by ECS instances of the other VPC.

## Can I adjust the specification of a router interface in the case of service spike? {#section_a21_ypb_12b .section}

Yes. Alibaba Cloud now supports upgrading or downgrading the specification of a router interface. You can change the specification of the initiator router interface at any time and the change takes effect immediately.

## Does Alibaba Cloud limit the transmission capacity of an Express Connect router interface? {#section_c21_ypb_12b .section}

Yes. Alibaba Cloud limits the data transmission capacity according to the specification of the router interface you purchased.

## Can I purchase a peering connection? {#section_t2n_bjp_m6w .section}

No. All purchasing of peering connections stopped on June 20, 2019. However, if you purchased peering connections before June 20, 2019, you can continue to use the purchased peering connections without being affected.

You can use Cloud Enterprise Network \(CEN\) instead to meet your needs. For more information, see [Migrate VPCs and VBRs to CEN](../../../../reseller.en-US/Best Practices/Migrate Express Connect peering connections to CEN/Migrate VPCs and VBRs to CEN.md#).

## How many peering connections can I create for a VPC? {#section_vt0_ntf_bc9 .section}

The maximum number of peering connections that can be created for a VPC is 10 by default. If you need to create more peering connections, go to the Express Connect console and on the [Quota Management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) page, apply to increase the **ec\_quota\_vroute\_ri\_num** quota.

## How many peering connections can I create for a Virtual Border Router \(VBR\)? {#section_dn2_dp8_31a .section}

The maximum number of peering connections that can be created for a VBR is 10 by default. If you need to create more peering connections, go to the Express Connect console and on the [Quota Management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) page, apply to increase the **ec\_quota\_vbr\_ri\_num** quota.

## How many peering connections can I create under one account? {#section_drl_v22_buf .section}

The maximum number of peering connections that can be created under one account is 20 by default. If you need to create more peering connections, go to the Express Connect console and on the [Quota Management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) page, apply to increase the **ec\_quota\_user\_ri\_num** quota.

