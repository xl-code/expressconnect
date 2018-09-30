# Access cloud services through physical connection {#concept_dzl_cjb_ydb .concept}

## AnyTunnel VIP {#section_i15_2jb_ydb .section}

AnyTunnel VIP belongs to 100.64.0.0/10 of each VPC. DNS, YUM, NTP, OSS, SLS, and other cloud services are all using IPs belonging to 100.64.0.0/10.

 If you need to access these cloud services from the peer end of the leased line, namely your local data center, you must set the router interface pointing to VPC as the next hop of the route destined for 100.64.0.0/10 after you create the VBR. You also need to set the router interface pointing to Alibaba Cloud as the next hop of the route destined for 100.64.0.0/10 on the gateway device of the local data center.

**Note:** Because 100.64.0.0/10 is a reserved CIDR block of VPC, you need to split it into 100.64.0.0/11 and 100.96.0.0/11 and configure two route entries on the VBR.

## Configure the route on the VBR {#section_mnn_hjb_ydb .section}

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation bar, select **Physical Connection** \> **Virtual Border Router**.
3.  Click **Manage** in the **Actions** column of the target VBR.
4.  On the VBR Details page, click **Add Route Entry** and configure the route entry. The following configurations are used in this tutorial:
    -   **Destination CIDR Block**: Enter 100.64.0.0/11 and 100.96.0.0/11 respectively.
    -   **Next Hop Direction**: To VPC
    -   **Next Hop**: Select the exit for data packets. In this tutorial, select the router interface on the VBR. 
5.  Click **OK** to complete the configuration.

## Configure the route on the customer-side access device of the leased line {#section_as1_vjb_ydb .section}

Add a static route pointing to Alibaba Cloud on the customer-side access device of the leased line:

```
ip route 100.64.0.0/10 {Alibaba Cloud-side IP address}
```

