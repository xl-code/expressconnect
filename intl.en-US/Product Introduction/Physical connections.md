# Physical connections {#concept_n3j_sry_xdb .concept}

A physical connection is the abstraction of the network circuits established between an Alibaba Cloud access point and your on-premises data center. To establish a physical connection, you have to apply for a leased line. A leased line is a cable rented from a network carrier that connects your on-premises network to an Alibaba Cloud access point.

With this leased line in place, you can create a virtual border router \(VBR\) to connect your on-premises IDC to Alibaba Cloud to build a hybrid cloud environment. Therefore, the cloud resources can access your on-premises network bypassing the Internet over a private network connection.

The physical connection does not go through the Internet. It is more secure, reliable, and fast with lower latency than typical Internet connections.

## Functions {#section_exb_zsq_ydb .section}

The physical connection provides the following functions:

-   Multiple connectivity models

    You can choose to use a point-to-point Ethernet connection or an MPLS VPN connection Physical connection supports Ethernet RJ45 electrical ports and LC-mode optical ports with 1 Mbps - 10 Gbps transmission rate.

-   Redundant connections

    Physical connection uses the equal-cost multi-path routing \(ECMP\) to achieve redundancy of two leased lines:

    -   If the two leased lines connect to different access points in a same region, then these two leased lines are redundant by default.

    -   If the two leased lines connect to the same access point in a same region, you can select the first leased line as the redundant connection when applying for the second leased line.


## Limits {#section_vrf_ctq_ydb .section}

The following are physical connection limitations:

-   Physical connections do not support SDH G.703 or V.35 interfaces.

-   Alibaba Cloud provides one or more access points in each accessible region. Different access points have different carrier restrictions. Before applying for leased line access, you must open a ticket to obtain the access point and carrier restriction information.


