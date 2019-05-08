# What is a physical connection? {#concept_n3j_sry_xdb .concept}

You can use a leased line from your service provider to establish a physical connection from your on-premises data center to an Alibaba Cloud access point. After the physical connection is established, you can create a Virtual Border Router \(VBR\) to connect your on-premises data center with Alibaba Cloud to build hybrid cloud networks. As a private network connection, the physical connection does not pass through the Internet. Compared with traditional Internet connections, the physical connection is safer, faster, more reliable, and has optimal network latency.

## Functions {#section_exb_zsq_ydb .section}

The physical connection interface of Express Connect \(through which an ISP leased line connects to an Alibaba Cloud access point\) provides the following functions:

-   Multiple connection modes

    You can use a point-to-point Ethernet connection or MPLS VPN connection. The physical connection supports RJ45 and LC optical ports over a maximum distance of 10 kilometers with a transmission rate from 1 Mbit/s to 100 Gbit/s.

-   Redundant connections

    The physical connection uses Equal-Cost Multi-Path routing \(ECMP\) to implement redundancy with two leased lines.

    -   If both leased lines are in the same region but connected to different access points, the leased lines automatically provide network redundancy.

    -   If both leased lines are connected to the same access point in the same region, you can select the first leased line as the redundant connection when applying for the second leased line.


## Limits {#section_vrf_ctq_ydb .section}

The physical connection interface of Express Connect has the following limits:

-   Physical connections do not support SDH G.703 or V.35 interfaces.

-   Different access points may have different service provider restrictions. Before applying for leased line access, you must open a ticket to obtain the target access point and corresponding restriction information of your service provider.


