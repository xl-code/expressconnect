# Physical connection {#concept_n3j_sry_xdb .concept}

You can use a leased line from your service provider to establish a physical connection from your local IDC to an Alibaba Cloud access point. After the physical connection is established, you can create a Virtual Border Router \(VBR\) to connect your local IDC with Alibaba Cloud to build hybrid clouds. As a private network connection, the physical connection does not pass through the Internet. Compared with traditional Internet connections, the physical connection is safer, faster, more reliable, and has less latency.

## Functions {#section_exb_zsq_ydb .section}

The Express Connect physical connection interface \(through which an ISP leased line connects to an Alibaba Cloud access point\) provides the following functions:

-   Multiple connection modes

    You can use a point-to-point Ethernet connection or MPLS VPN connection. The physical connection supports RJ45 and LC optical ports \(maximum distance: 10 km\) with a transmission rate from 1 Mbit/s to 100 Gbit/s.

-   Redundant connections

    The physical connection uses Equal-Cost Multi-Path routing \(ECMP\) to implement redundancy with two leased lines.

    -   If both leased lines are connected to different access points in the same region, the leased lines are naturally redundant to each other.

    -   If both leased lines are connected to the same access point in the same region, you can select the first leased line as the redundant connection when applying for the second leased line.


## Limits {#section_vrf_ctq_ydb .section}

The physical connection interface has the following limits:

-   Physical connections do not support SDH G.703 or V.35 interfaces.

-   Alibaba Cloud provides one or more access points in each accessible region. Different access points have different service provider restrictions. Before applying for leased line access, you must submit a ticket to obtain an access point and the restriction information of your service provider.


