# Virtual border router {#concept_oqw_try_xdb .concept}

A virtual border router \(VBR\) is a product mapping of the leased line that you have applied to access a VSwitch. You can think of it as a router between your customer-premises equipment \(CPE\) and the VPC, which serves as a bridge for exchanging data between the on-premises IDC and the VPC.

Same as the VRouter in a VPC, VBR also has a route table. You can configure route entries for it to forward traffic.

## Functions {#section_pdc_ftq_ydb .section}

VBR provides following functions:

-   Exchange data between a VPC and an on-premises IDC as a router.

-   In the layer-3 subinterface mode, VBR can identify or bind VLAN tags.

-   Decide the port mode for the leased line: layer-3 interface or VLAN-based layer-3 subinterface.

-   Support BGP routing.


## Limits {#section_ohj_jtq_ydb .section}

-   Each VBR have only one routing table.

-   The maximum number of custom routing entries in one routing table is 48.

-   Source address-based policy routing is not supported.


