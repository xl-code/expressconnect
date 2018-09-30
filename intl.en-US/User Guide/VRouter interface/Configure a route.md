# Configure a route {#task_nfp_vcz_xdb .task}

After creating router interfaces, you need to configure a route for the VRouter.

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri). 
2.  Enter the Router Interface page. 
3.  Click **Route Configuration** next to the target router interface. 
4.  Click **Add Route Entry**. 
5.  In the displayed dialog box, configure the following information: 
    -   **Destination CIDR Block**: The VSwitch CIDR block of the peer VPC.
    -   **Next Hop Type**: Select **Router Interface**.
    -   **Router Interface**: If you have not applied a redundant leased line, select **General Routing**. If you have applied a redundant leased line, select **ECMP Routing**. In the drop-down list, select the exit for data packets, that is, select the local router interface.

        **Note:** Between two VPCs, only one pair of router interfaces are allowed to be successfully connected, therefore, the two interfaces are each other's peer interfaces by default. You only need to select the local router interface, then data packets will be automatically routed to the peer router interface.

6.  Click **OK**. 

