# Manage Pay-As-You-Go instances {#task_j2d_hk3_dfb .task}

You can delete your Pay-As-You-Go instances, change their bandwidths, or change their billing method to Subscription.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VPC-to-VPC** or **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Select the region where your instance is located and find your target instance.
4.  Click ![](images/12053_en-US_source.png) and select the operation you want to perform: 
    -   **Initiate Connection**: When creating a peering connection between two different accounts, you must initiate the connection from the initiator after adding the peer instance. The connection can be initiated only from the initiator instance.
    -   **Upgrade/Downgrade**: Change the bandwidth of the initiator instance.
    -   **Switch to Subscription**: Change the billing method of the initiator to Subscription.
    -   **Suspend Initiator/Acceptor**: Suspend the activated instance. Data is no longer forwarded after the suspension.
    -   **Activate Initiator/Acceptor**: Activate the suspended instance. Data forwarding is restored after the activation.
    -   **Delete**: Delete the unconnected or suspended instance.

