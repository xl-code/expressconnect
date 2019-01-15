# Billing of peering connections {#concept_ekt_hyq_ydb .concept}

In the process of peering connection, Alibaba Cloud charges for the initiator instance but does not charge for the acceptor instance.

## Billing methods {#section_op1_jyq_ydb .section}

|Billing method|Description|Upgrade or downgrade|Overdue payment instruction|
|:-------------|:----------|:-------------------|:--------------------------|
|Subscription|Subscription on a monthly basis and the billing unit is USD/month.| Temporary upgrades are supported.

 Upgrades or downgrades are supported after subscription renewal.

 | -   When the initiator instance is overdue for more than 24 hours, it will stop forwarding data and be locked.
-   If you renew your account within 24 hours after the bill is overdue, your configuration will not be affected.
-   After your account is settled, the initiator instance will immediately restart data forwarding and be unlocked.
-   If the initiator instance is overdue and locked for more than 15 days, it will be reclaimed. The configuration will be cleared and cannot be restored.

 |

## Peering connection fee {#section_oc1_tyq_ydb .section}

In the process of peering connection, Alibaba Cloud charges for the initiator instance but does not charge for the acceptor instance. The fee depends on the bandwidth of the initiator instance and the distance between the two instances. The fee of VPC interconnection in the same region is lower than that of VPC interconnection between different regions.

-   Cross-region interconnections are charged according to the prices shown on the purchase page. If you have any problem, contact your customer manager.

**Note:** Peering connections between the China \(Beijing\) region and the China \(Zhangjiakou\) region with bandwidth less than 2 Gb are free of charge before December 31, 2020.

-   Same-region interconnections are charged according to the price listed in the following table. This fee will not be charged until December 31, 2020.

|Bandwidth \(Gbps\)|Initiator instance fee \(USD/month\)|
|:-----------------|:-----------------------------------|
|1|70|


