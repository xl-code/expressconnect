# Billing {#concept_wtm_h1r_ydb .concept}

Express Connect only supports the Subscription billing method. Only the initiator router interface is charged and the receiver router interface is not charged.

**Note:** The Pay-As-You-Go billing method is used for creating a receiver router interface for multi-tenant VPC interconnection or physical connection. On the Pay-As-You-Go page, you can configure the receiver configurations, and do not need to pay for the receiver.

## Billing for a physical connection {#section_oc1_tyq_ydb .section}

The fee of the physical connection \(connecting an on-premises IDC to a VPC\) includes the physical connection \(leased line\) fee and the router interface fee, as shown in the following table.

|Charge item|Description|
|:----------|:----------|
|Leased line|Laying fee|Charged by the network carrier or partner based on bandwidth and distance.|
|Initial installation fee| Charged by Alibaba Cloud. 15,000 yuan is charged on each leased line.

 On-site construction and maintenance fee. For port leasing fee, see [Table 1](#table_u3x_4zq_ydb). Now physical switch ports in Alibaba datacenters are free of charge.

 |
|In-house cable leasing fee|Charged by the network carrier or partner. The leasing fee varies by the carrier.|
|Router interface| The initiator router interface fee charged by Alibaba Cloud based on the interface specification and distance.

 The price here is a reference, take the price on the purchase page as standard. If you have any problems, contact your customer manager.

 **Note:** When the virtual border router and the VPC are in the same region, no distance fee is charged.

 |

**Port leasing fee**

The port leasing fee is charged on a daily basis, as shown in the following table. Now physical switch ports in Alibaba data centers are free of charge.

|Specification\(Gbps\)|Price before October 1, 2018\(USD/Month\)|Price after October 1, 2018\(USD/Month\)|
|:--------------------|:----------------------------------------|:---------------------------------------|
|1.|0|20|
|October|0|170|

## Billing for VPC interconnection {#section_f21_tyq_ydb .section}

Only the initiator router interface is charged, and the receiver router interface is not charged, when using Express Connect to connect two VPCs.

The total fee depends on the distance and interface specification. The fee for connecting two VPCs in the same region is lower than the fee for connecting two VPCs in different regions.

The price here is a reference, take the price on the purchase page as standard. If you have any problems, contact your customer manager.

**Note:** Before April 1, 2019, the interconnection between two VPCs or between a VPC and a VBR in the same region is free of charge.

|Specification \(Gbps\) |Price before April 1, 2019 \(RMB/month\)|Price after April 1, 2019 \(RMB/month\)|
|:----------------------|:---------------------------------------|:--------------------------------------|
|1|0|450|
|2|0|900|

## Overdue payments {#section_clf_dbr_ydb .section}

-   The leased line and the initiator router interface will be stopped and locked when your bill is overdue. After you recharge your overdue bill, the instance will be automatically restarted.

-   If you do not recharge your overdue bill within 15 days after the service is stopped, the resources will be released, and related route entries will be deleted and cannot be recovered.

**Note:** When the initiator router interface is locked, the receiver router interface cannot receive any traffic.


