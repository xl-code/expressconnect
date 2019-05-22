# Configure health checks {#task_b1m_mv3_5fb .task}

To ensure that traffic is distributed to the other physical connection when one physical connection fails, you must configure health checks for VBRs.

Make sure that you have established redundant physical connections and added ECMP routes directing to the on-premises data center in the VPC.

Alibaba Cloud sends a ping packet to the customer-side IP address of the on-premises data center from each health check IP address every two seconds. If eight successive ping packets on one leased line fail to give responses, the traffic is distributed to the other leased line.

**Note:** If Control Plane Policing \(Copp\) \(such as Cisco devices\) or Local Attack Defense Policy \(Huawei devices\) is configured on the on-premises data center, health check packets may be discarded and then the health check link shocks. We recommend that you cancel the control side speed limitation on the network device of the on-premises data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62556/155849235431622_en-US.png)

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Locate the target peering connection and click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/155849235412053_en-US.png)** \> **Health Check**.
4.  Click **Configure** and then configure the health check based on the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |**Source IP**|Any idle private IP address in the VPC.|
    |**Destination IP**|The interface IP address of the network device of the on-premises data center. If you need to perform an ICMP health check from your on-premises data center to the VPC to check if the connection is normal, we recommend that you set the **Destination IP** as the source IP address used for health checks of the VPC, and configure a route that points to this address.

 |


