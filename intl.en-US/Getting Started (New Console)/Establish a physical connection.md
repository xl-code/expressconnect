# Establish a physical connection {#concept_zmz_dzs_ggb .concept}

This topic describes the physical connection methods you can use to access Alibaba Cloud through Express Connect. Specifically, you can apply for a dedicated physical line from your service provider or providers, or use Express Cloud Connect \(ECC\).

## Use Express Cloud Connect {#section_qj5_kzs_ggb .section}

You can connect to Alibaba Cloud through ECC and an Internet connection, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83738/156462413145512_en-US.png)

## Apply for a dedicated physical line {#section_ttl_3dt_ggb .section}

You can apply for a dedicated physical line from your service provider or providers, and connect your on-premises data center to an Alibaba Cloud access point through this dedicated line. This physical connection method needs to occupy a physical port of Alibaba Cloud. The following figure shows the overall connection process.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83738/156462413135446_en-US.png)

## Differences between the two physical connection methods {#section_hwq_hft_ggb .section}

|Item|ECC|Dedicated line|
|:---|:--|:-------------|
|User experience|ECC provides you with an end-to-end cloud access service, which covers the whole connection process from access equipment debug, connection of user-side data centers with Alibaba Cloud-side data centers, and cloud-side configurations. You do not need to apply for a dedicated line from service providers.|Multiple parties are involved.|
|Function| -   SD-WAN technology: high reliability through backup bandwidth and links; simplified operation and maintenance through centralized configuration and monitoring; high security through encrypted links.
-   Alibaba Cloud services: OSS, DTS, RDS, DNS, and NAT.

 |Connects on-premises data centers and VPCs.|
|Billing|ECC is based on Smart Access Gateway. No initial installation fee, resource occupation fee, or outbound traffic fee is charged. Only ECC service fee is charged. For more information, see [Billing of Express Cloud Connect instances](../../../../intl.en-US/Pricing/Billing of Express Cloud Connect instances.md#)|An initial installation fee \(one-time charge\) and a resource occupation fee \(on a monthly basis\) are charged by Alibaba Cloud. Other construction and bandwidth rental fees are charged by the service provider. For more information, see [Billing of physical connections](../../../../intl.en-US/Pricing/Billing of physical connections.md#).

 |
|Process|For detailed procedures, see [EN-US\_TP\_162666.md\#](intl.en-US/Express Cloud Connect (Beta)/Activate Express Cloud Connect.md#).|For detailed procedures, see [Apply for a physical connection interface](../../../../intl.en-US/Physical Connection/Apply for a physical connection interface.md#).|

