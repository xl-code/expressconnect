# Manage Subscription-billed instances {#task_j2d_hk3_dfb .task}

You can change the bandwidth values of your Subscription-billed instances and pay for the change.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VPC-to-VPC** or **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Select the region of the target peering connection and find the target peering connection.
4.  Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/156113021112053_en-US.png) and select the operation you want to perform: 
    -   **Renew**: When the initiator instance is overdue for more than 24 hours, the physical connection interface stops forwarding data and is locked. To avoid affecting your business, we recommend that you renew your instance in a timely manner.
    -   **Renew and Upgrade/Downgrade**: Change the bandwidth while you renew your instance. The change takes effect in the next billing cycle.
    -   **Upgrade**: Increase the bandwidth of the initiator.
    -   **Suspend Initiator/Acceptor**: Suspend the activated initiator or acceptor. Data is no longer forwarded after the suspension.
    -   **Activate Initiator/Acceptor**: Activate the suspended initiator or acceptor. Data forwarding is restored after the activation.
    -   **Temporarily Upgrade**: Temporarily increase the bandwidth of the initiator.

        The upgrade interval is two hours. The price is charged by the hour. The upgrade takes effect immediately after the payment. Services are not interrupted during the upgrade.

        When the upgrade duration ends, the initiator automatically returns to the original bandwidth. Your service will not be interrupted when the initiator returns to the original bandwidth, but intermittent disconnections may occur. We recommend that your applications have re-connection functionalities.


