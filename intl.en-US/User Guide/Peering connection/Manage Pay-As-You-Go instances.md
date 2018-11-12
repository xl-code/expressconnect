# Manage Pay-As-You-Go instances {#task_j2d_hk3_dfb .task}

You can delete your Pay-As-You-Go instances, change their bandwidths, or change their billing method to Subscription.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left navigation pane, click**VPC Peering Connections** \> **VPC-to-VPC** or **VPC Peering Connections** \> **VBR-to-VPC**. 
3.  Select the region where your instance is located and find your target instance. 
4.  Click ![](images/12053_en-US.png) and select the operations you want: 
    -   **Initiate Connection**: After you establish a peering connection between different accounts and add the peer instance, you need to initiate a connection from the initiator. The connection can be initiated only from the initiator.
    -   **Upgrade/Downgrade**: Change the bandwidth of the initiator instance.
    -   **Switch to Subscription**: Change the billing method of the initiator instance to Subscription.
    -   **Suspend Initiator/Acceptor**: Suspend the activated instance. No data is forwarded after suspension.
    -   **Activate Initiator/Acceptor**: Activate the suspended instance. Data forwarding will be restored after activation.
    -   **Delete**: Delete the unconnected or suspended instance.

