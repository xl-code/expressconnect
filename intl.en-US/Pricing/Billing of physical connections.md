# Billing of physical connections {#concept_ekt_hyq_ydb .concept}

The billing of physical connections involves fees charged by Alibaba Cloud and third parties.

## Billing method {#section_op1_jyq_ydb .section}

|Billing method|Description|Upgrade or downgrade|Overdue payment process|
|:-------------|:----------|:-------------------|:----------------------|
|Subscription|Monthly or yearly subscription with the billing unit of USD/month| Not supported

 | -   You will be notified about payment for a physical connection 15 days, 7 days, 3 days, and 1 day before the payment is due.
-   If the payment for a physical connection is not settled within 15 days after the physical connection expires, the physical connection is stopped.

 **Note:** Within the one month after a physical connection is stopped, the corresponding devices, resources, and configurations associated with the physical connection are reserved \(that is, the resources are not released\).

 |

## Billing items {#section_c2z_dss_2fb .section}

The physical connection service involves Alibaba Cloud fees and third-party fees.

-   Alibaba Cloud fees

    The fee for a physical connection is charged by Alibaba Cloud and includes an initial installation fee, resource occupation fee, and outbound traffic fee.

    -   If you access Alibaba Cloud through a dedicated port, you need to pay a one-time initial installation fee for the physical connection. The resource occupation fee is charged on a monthly basis.
    -   If you access Alibaba Cloud through an NSP partner with a shared port, you only need to pay for the outbound traffic fee, which is charged on a monthly basis.
-   Third-party fees

    The fees charged by third parties \(telecom operators, partners, and data center operators\) include the **leased-line fee** and **indoor cable rental fee**. For more information, consult the third party.


## Pricing of dedicated access ports {#section_acg_bcc_p2b .section}

Dedicated access port fees include [Table 1](#table_p1x_rst_gfb) and [Table 2](#table_awd_lmt_gfb).

|Interface specification|Price \(USD\)|
|:----------------------|:------------|
|1G and below|1,500|
|10G|1,500|
|40G|1,500|
|100G|1,500|

|Charged item|Interface specification|Subscription \(USD/month\)|
|:-----------|:----------------------|--------------------------|
|Resource occupation fee \(Mainland China\)|1G and below|85|
|10G|720|
|40G|2,450|
|100G|5,200|
|Resource occupation fee \(Outside Mainland China\)|1G and below|210|
|10G|1,600|
|40G|5,500|
|100G|11,700|

**Note:** Billing for the resource occupation fee starts April 1, 2019.

## Pricing of shared access ports by partners {#section_p24_mlt_gfb .section}

|Charged item|Price|
|:-----------|:----|
|Outbound traffic fee|0.015 USD/GB|

**Note:** No outbound traffic fee is charged before October 1, 2019.

## Third-party fees {#section_prn_fkt_gfb .section}

Third-party fees include the leased-line fee and indoor cable rental fee. For more information, contact the third party.

|Charged item|Description|
|:-----------|:----------|
|Leased-line fee|Charged by telecom operators or partners. The lease fee depends on the bandwidth and distance.|
|Indoor cable rental fee| Charged by IDC operators or partners.

 For more information, consult the third party.

 |

