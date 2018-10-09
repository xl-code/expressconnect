# Add a route entry {#task_vsk_m21_ydb .task}

You need to perform this operation twice. Add one route entry directing to the VPC and add one route entry directing to the local data center, so that the local data center can communicate with the VPC through the VBR.

After configuring the route on the VBR according to this tutorial, you also need to configure the route on the local data center. Configure a route pointing to the VPC CIDR block on the physical access device of the on-premises IDC. You can configure a static route or BGP dynamic routing to forward data from the local data center to the VBR:

1.  Log on to [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri). 
2.  In the left-side navigation pane, select **Virtual Border Router**. 
3.  Select the target VBR in the VBR list. 
4.  Click **Manage**. 
5.  In the page of VBR details, click **Add Route Entry**. 
6.  In the displayed dialog box, enter the following information: 
    -   **Destination CIDR Block**: The CIDR block cannot include any public IP.
    -   **Next Hop Direction**: To forward data to VPC, select **To VPC**. To forward data to the leased line, select **Leased Line**.
    -   **Next Hop**: To forward data to VPC, select the data exit on the VBR, namely, a router interface of the VBR.
7.  Click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13848/15390473793963_en-US.png)


