# Select an access point {#concept_w1y_yht_ggb .concept}

This topic describes how to select a suitable access point. When you apply for a physical connection interface, you need to select an Alibaba Cloud access point. To select a suitable access point, you must consider some factors, such as the region, service provider, and port.

## Scenario {#section_kgn_3jt_ggb .section}

In this example, an on-premises data center needs to connect to an Alibaba Cloud VPC that belongs to the China \(Beijing\) region. The on-premises data center is located in Beijing Yizhuang and run by China Unicom. The connection needs a 10 Gbit/s bandwidth.

For more information about how to apply for a physical connection interface, see [Connect an on-premises data center to a VPC through a physical connection](intl.en-US/Getting Started (New Console)/Connect an on-premises data center to a VPC through a physical connection.md#).

## Step 1 Select a region {#section_etb_clt_ggb .section}

When you select an access point, you need to first select a region. We recommend that you select a region that is closest in geographic proximity to your on-premises data center. In this example, select China \(Beijing\).

Note that different access points have different service providers and connection bandwidths. The purchase page displays available service providers and bandwidth values.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83760/156462414335455_en-US.png)

## Step 2 Select a service provider {#section_cnv_qmt_ggb .section}

After selecting the region, you need to select a service provider who provides the leased line. Generally, China Unicom, China Telecom, China Mobile, and some local service providers are available.

In this example, the on-premises data center to be connected is run by China Unicom. Therefore, select China Unicom or a neutral access point. The access points that support China Unicom include Beijing-Daxing-A, Beijing-Daxing-B, Beijing-Fengtai-A, Beijing-Yizhuang-A, and Beijing-Yizhuang-B.

## Step 3 Select a port {#section_pzy_w4t_ggb .section}

Select an electrical or optical port:

-   All electrical ports use MSTP links. At Alibaba Cloud data centers where access points are located, service providers convert the optical cable of the transmission network to a low-bandwidth network cable with an RJ45 interface. According to the industry standard, RJ45 interfaces are used for the bandwidth lower than 100 Mbit/s. Therefore, if you need a low bandwidth, we recommend that you select a 100M electrical port.

    The switches at Alibaba Cloud data centers of access points support 10GE electrical ports by default. The ports can be 100M, 1000M, or 10G and are auto-sensing. If you select 100Base-T, the port adapt itself to a speed of 100M. If you select 1000Base-T, the port adapt itself to a speed of 1000M.

    **Note:** 

    -   100Base-T: Indicates a 100M electrical port.
    -   1000Base-T: Indicates a 1000M electrical port.
-   Optical ports are commonly known as bare optical fibers. If you choose optical ports, service providers do not need to convert the optical cable of the transmission network at the access points. Users can use optical cables directly. Theoretically, the speed of an optical path is unlimited. The speed only depends on the negotiation of optical modules at both ends of the connection. The speed can be 1000M, 10G, 40G, or 100G. Alibaba Cloud data centers provide 1000M and 10G single-mode modules with a transmission distance of 10 km free of charge. If you need modules with a longer distance, you need to purchase the modules by yourself.


According to the preceding description, available access points for the on-premises data center in this example include Beijing-Daxing-A, Beijing-Daxing-B, Beijing-Fengtai-A, Beijing-Yizhuang A, and Bejing-Yizhuang-B. The available ports are 10G optical ports.

