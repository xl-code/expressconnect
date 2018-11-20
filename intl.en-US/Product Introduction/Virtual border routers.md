# Virtual border routers {#concept_oqw_try_xdb .concept}

Alibaba Cloud isolates the physical connection ports of its customers and abstracts these ports into Virtual Border Routers \(VBRs\) based on the three-layer overlay and switch virtualization technology of the Software Defined Network \(SDN\) architecture. A VBR is a router between the Customer-Premises Equipment \(CPE\) and the VPC, and functions as a data forwarding bridge from the VPC to the local IDC.

Similar to the router in a VPC, a VBR also has a route table. You can configure route entries in the route table to forward VBR traffic.

## Functions {#section_pdc_ftq_ydb .section}

VBR provides the following functions:

-   Exchanges data packets as an intermediate router between the VPC and the local IDC.

-   Attaches or identifies Virtual Local Area Network \(VLAN\) tags in Layer-3 sub-interface mode.

-   Decides the port mode of the physical connection: Layer-3 route interface or VLAN-based Layer-3 sub-interface.

-   Supports Border Gateway Protocol \(BGP\).

    BGP is a dynamic routing protocol based on Transmission Control Protocol \(TCP\). It is mainly used to exchange routing information and network accessibility information among autonomous systems. You can use BGP to implement intranet connection between the local IDC and the VBR. BGP can help you build hybrid clouds in a more efficient, flexible, and reliable manner.


## Limits {#section_ohj_jtq_ydb .section}

-   Source address policy routing is not supported.

-   Each VBR has only one route table.

-   Each route table supports 48 custom route entries.

-   VBR can establish BGP peers only with the peered local IDC of a physical connection. Static routing is still needed between the VBR and the VPC.

-   The supported BGP version is BGP4.

-   The VBR supports IPv4 BGP, but does not support IPv6 BGP.

-   A maximum of eight BGP peers can be created under each VBR.

-   A maximum of 100 dynamic route entries can be added to a BGP peer.

-   The Autonomous System Number \(ASN\) of Alibaba Cloud is 45104. It supports the transmission of 2-byte or 4-byte ASNs from the customer side.


