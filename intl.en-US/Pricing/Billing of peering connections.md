# Billing of peering connections {#concept_ekt_hyq_ydb .concept}

The billing method of peering connections is Subscription.

## Billing method {#section_op1_jyq_ydb .section}

|Billing method|Description|Upgrade or downgrade|Overdue payment instruction|
|:-------------|:----------|:-------------------|:--------------------------|
|Subscription|Monthly or yearly subscription with the billing unit of USD/month| Real-time upgrades are supported.

 Temporary upgrades are supported.

 Upgrades or downgrades are supported after subscription renewal.

 Real-time downgrade is not supported

 | -   When the initiator instance is overdue for more than 24 hours, it will stop forwarding data and be locked.
-   If you recharge your account within 24 hours after the bill is overdue, your configuration will not be affected.
-   After your account is settled, the initiator instance will immediately restart data forwarding and be unlocked.
-   If the initiator instance is overdue and locked for more than 15 days, it will be reclaimed. The configuration will be cleared and cannot be restored.

 |

## Peering connection fee {#section_oc1_tyq_ydb .section}

In the process of peering connection, Alibaba Cloud charges for the initiator instance but does not charge for the acceptor instance. The fee depends on the bandwidth of the initiator instance and the distance between the two instances. The fee of VPC interconnection in the same region is lower than that of VPC interconnection between different regions.

-   Cross-region interconnections are charged according to the prices shown on the purchase page. If you have any problem, contact your customer manager.

**Note:** Before December 31, 2020, VPC interconnection between North China 2 \(Beijing\) and North China 3 \(Zhangjiakou\) is free.

-   Same-region interconnections are charged according to the price listed in the following table. This fee will not be charged until December 31, 2020.

|Bandwidth \(Gbps\)|Initiator instance fee \(USD/month\)|
|:-----------------|:-----------------------------------|
|1|70|


