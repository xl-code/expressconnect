# Billing of peering connections {#concept_ekt_hyq_ydb .concept}

Peering connection supports the Subscription billing method.

## Billing method {#section_op1_jyq_ydb .section}

|Billing method|Description|Upgrade or downgrade|Overdue instruction|
|:-------------|:----------|:-------------------|:------------------|
|Subscription|Subscription on a monthly basis| Real-time upgrade is supported.

 Temporary upgrade is supported.

 Renewal upgrade or downgrade is supported.

 | -   When the initiator instance is overdue for more than 24 hours, the instance will stop forwarding data and be locked.
-   If you renew your account within 24 hours after the bill is overdue, your configuration will not be affected.
-   The service will be restarted immediately after you renew your account.
-   If the initiator instance is overdue and locked for more than 15 days, the initiator instance will be reclaimed, the configurations will be cleared and cannot be recovered.

 |

## Peer connection fee {#section_oc1_tyq_ydb .section}

In the process of peering connection, Alibaba Cloud only charges fee on the initiator instance and does not charge the receiver instance. The fee is charged according to the bandwidth of the initiator instance and the distance between the two instances. The costs of VPC interconnection in the same region is lower than that of VPC interconnection across regions.

-   For the prices of cross-region interconnection, take the price on the purchase page as standard. If you have any problem, contact your customer manager.

-   For the prices of same-region interconnection, see the price in the following table. This fee is not charged until April 1, 2019.

|Bandwidth \(Gbps\)|Initiator instance fee \(USD/month\)|
|:-----------------|:-----------------------------------|
|1|70|


