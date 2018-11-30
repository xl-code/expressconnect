# Manage Subscription instances {#task_j2d_hk3_dfb .task}

You can change the bandwidths of your Subscription instances and pay for the change.

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC** or **VPC Peering Connections** \> **VBR-to-VPC**. 
3.  Select the region where your instance is located and find your target instance. 
4.  Click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/154355106912053_en-US.png) and select the operation you want to perform: 
    -   **Renew**: When the initiator instance is overdue for more than 24 hours, the physical connection interface stops forwarding data and is locked. To avoid affecting your business, we recommend that you renew your account in a timely manner.
    -   **Renew and Upgrade/Downgrade**: Change the bandwidth while you renew your account. The change takes effect in the next billing cycle.
    -   **Upgrade**: Increase the bandwidth of the initiator instance.
    -   **Suspend Initiator/Acceptor**: Suspend the activated instance. Data will no longer be forwarded after the suspension.
    -   **Activate Initiator/Acceptor**: Activate the suspended instance. Data forwarding will be restored after the activation.
    -   **Temporarily Upgrade**: Temporarily increase the bandwidth of the initiator instance.

        The upgrade interval is two hours. The price is charged by the hour. It will take effect immediately after the payment. Services will not be interrupted during the upgrade.

        When the upgrade duration ends, the initiator instance automatically returns to the original bandwidth. Your service will not be interrupted when the initiator instance returns to the original bandwidth, but intermittent disconnection may occur. We recommend that your applications have re-connection functionalities.


