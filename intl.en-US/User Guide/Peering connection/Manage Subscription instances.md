# Manage Subscription instances {#task_j2d_hk3_dfb .task}

You can change the bandwidth of your Subscription instance and pay for it.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC** or **VPC Peering Connections** \> **VBR-to-VPC**. 
3.  Select the region where your instance is located and find your target instance. 
4.  Click ![](images/12053_en-US.png) and select the operations you want to perform: 
    -   **Renew**: When the initiator instance is overdue for more than 24 hours, the physical connection interface stops data forwarding and is locked. To avoid affecting your business, we recommend that you renew your account in time.
    -   **Renew and Upgrade/Downgrade**: Change the bandwidth when you are renewing your account. The change takes effect in the next billing cycle.
    -   **Upgrade**: Increase the bandwidth of the initiator instance.
    -   **Suspend Initiator/Acceptor**: Suspend activated instances. Data will no longer be forwarded for the instance after suspension.
    -   **Activate Initiator/Acceptor**: Activate suspended instances. Data forwarding will be restored after activation.
    -   **Temporarily Upgrade**: Temporarily increase the bandwidth of the initiator instance.

        The upgrade interval is two hours and you will be charged in hourly rate for the upgrade. Your business will not be interrupted during the upgrade.

        When the time is up, the router interface automatically changes to the original bandwidth. Your business will not be interrupted when the router interface returns to the original bandwidth. But intermittent disconnection may happen. So we recommend that your background applications have re-connection function.


