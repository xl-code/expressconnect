# Billing of peering connections {#concept_ekt_hyq_ydb .concept}

When you set a peering connection, Alibaba Cloud charges fees for the initiator instance, but does not charge fees for the acceptor instance.

## Billing method {#section_op1_jyq_ydb .section}

|Billing method|Description|Upgrade or downgrade|Overdue payment process|
|:-------------|:----------|:-------------------|:----------------------|
|Subscription|Monthly or yearly subscription with the billing unit of USD/month| Renewal is supported.

 | -   When payment for the peering connection is overdue, the initiator instance stops forwarding data 15 days after the date at which the payment is due, and the instance is automatically released after 15 days of downtime. Reminders are sent on the 8th, 12th, and 14th days after the expiration date and downtime date.
-   After you renew the peering connection, the initiator instance is restored immediately.
-   If the initiator instance is locked for more than 15 days after the date at which the payment is due, it is reclaimed by Alibaba Cloud. The configuration is then cleared and the connection cannot be restored.

 |

## Peering connection fee {#section_oc1_tyq_ydb .section}

When you set a peering connection, Alibaba Cloud charges fees for the initiator instance, but does not charge fees for the acceptor instance. The fee depends on the bandwidth of the initiator instance and the distance between the two instances. The fee for interconnected VPCs in the same region is lower than that of VPCs connected across different regions.

-   Cross-region interconnections are charged according to the prices displayed on the [purchase page](https://common-buy.aliyun.com/?spm=5176.9843921.0.0.2147160atVdZGO&commodityCode=ri_pre#/buy). If you have any issues, open a ticket.

**Note:** Peering connections that are established between the China \(Beijing\) region and the China \(Zhangjiakou\) region with a bandwidth value of 2 Gbit/s or less than 2 Gbit/s are free of charge before December 31, 2020.

-   Same-region interconnections are charged according to the price listed in the following table. This fee will not be charged until December 31, 2020.

|Bandwidth \(Gbit/s\)|Initiator instance fee \(USD/month\)|
|:-------------------|:-----------------------------------|
|1|70|


