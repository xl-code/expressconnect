# BGP概述 {#concept_lcr_px1_ydb .concept}

BGP（Border Gateway Protocol）是一种基于TCP协议的动态路由协议，主要应用于不同自治域间交换路由信息和网络可达信息。在物理专线接入的过程中，您可以使用BGP来实现本地数据中心与边界路由器（VBR）之间的内网互连。BGP可以帮您更高效、灵活且可靠地搭建混合云。

## BGP组和BGP邻居 {#section_pfm_tx1_ydb .section}

BGP组主要用于简化BGP配置，将需要不断重复的配置合并到一个BGP组后，可以减少配置复杂度。您只需根据ASN建立一个BGP组，然后将符合条件的BGP邻居加入此BGP组即可。加入BGP组之后，BGP邻居将继承BGP组的配置，您不再需要单独配置BGP邻居。

## 限制 {#section_fzt_5x1_ydb .section}

-   VBR仅支持与物理专线对端的本地数据中心建立BGP邻居，VBR与VPC之间仍需使用静态路由。
-   VBR支持的BGP版本为BGP4。
-   VBR支持IPv4 BGP，不支持IPv6 BGP。
-   每个VBR下最多建立8个BGP邻居。
-   每个BGP邻居的动态路由条数上限为100条。
-   阿里云侧ASN（Autonomous System Number）为：45104，可接受用户侧传递2字节或4字节的ASN。

