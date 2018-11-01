# Physical connection {#concept_n3j_sry_xdb .concept}

You can use a leased line provided by your service provider to connect your local IDC to an Alibaba Cloud access point to establish a physical connection. After the physical connection is established, you can create a Virtual Border Router \(VBR\) to connect your local IDC with Alibaba Cloud to build a hybrid cloud. As a private-network connection, the physical connection does not pass through the public network. Therefore, compared with traditional public network connections, physical connection is safer, more reliable, and faster with reduced latency.

## Functions {#section_exb_zsq_ydb .section}

The physical connection interface of Express Connect \(physical interface accessing an Alibaba Cloud access point through a leased line of a service provider\) provides the following functions:

-   Multiple connection modes

    You can use a point-to-point Ethernet connection or MPLS VPN connection. The physical connection supports Ethernet RJ45 electrical ports and LC optical ports \(10 km\) with a transmission rate of 1 Mbit/s to 100 Gbit/s.

-   Redundant connections

    The physical connection uses the Equal-Cost Multi-Path routing \(ECMP\) to implement redundancy of two physical lines:

    -   If the two leased lines are connected to different access points in the same region, both lines are redundant by default.

    -   If the two leased lines are connected to the same access point in the same region, you can select the first leased line as the redundant connection when applying for the second leased line.


## Restrictions {#section_vrf_ctq_ydb .section}

The restrictions on using physical connection interfaces are described as follows:

-   Physical connections do not support SDH G.703 or V.35 interfaces.

-   Alibaba Cloud provides one or more access points in each accessible region. Different access points have different service provider restrictions. Before applying for leased line access, you must open a ticket to obtain the access point and service provider restriction information.


