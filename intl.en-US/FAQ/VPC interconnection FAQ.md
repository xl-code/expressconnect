# VPC interconnection FAQ {#concept_h5w_vpb_12b .concept}

## Does the data transferred by Express Connect go through the Internet? {#section_vd1_ypb_12b .section}

No. Data on Express Connect is transmitted only inside Alibaba Cloud data centers or over lease lines among the data centers and does not pass through the Internet. This avoids data leakage during transmission and provides better network quality than the Internet.

## Does Express Connect support multi-tenant VPC intranet connection? {#section_wd1_ypb_12b .section}

Yes. Express Connect supports establishing an intranet connection between VPCs under the same account or different accounts. For more information, see [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13830.md\#](../../../../intl.en-US/Peering connections/Interconnect two VPCs under the same account.md#).

## Does Express Connect support cross-region VPC intranet connection? {#section_xd1_ypb_12b .section}

Yes. Express Connect supports establishing an intranet connection between VPCs in the same region or different regions. You can create a router interface on the VRouter of each VPC respectively and build Express Connect through Alibaba Cloud's backbone transmission network to achieve secure, reliable, fast, and convenient communication between the VPCs.

## If I use Express Connect for VPC intranet connection, what resources can the two sides access? {#section_yd1_ypb_12b .section}

ECS instances on both sides can access the ECS instances, Server Load Balancer instances, and RDS instances of the other side.

-   Server Load Balancer instances on one side cannot use ECS instances of the other side as backend servers.
-   ECS instances of one side cannot access cloud product instances other than the ECS instances, Server Load Balancer instances, and RDS instances of the other side. More instances will be supported in the future.

## Can I adjust the specification of a router interface in the case of service spike? {#section_a21_ypb_12b .section}

Alibaba Cloud now supports upgrading or downgrading the specification of a router interface. You can change the specification of the initiator router interface at any time as needed and the change takes effect immediately.

## Does Alibaba Cloud limit the transmission capacity of an Express Connect router interface? {#section_c21_ypb_12b .section}

Alibaba Cloud limits the data transmission capacity according to the specification of the router interface purchased by you.

