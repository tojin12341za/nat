# Bind an EIP {#task_o3q_3xy_ydb .task}

Before configuring DNAT or SNAT entries, you must bind an EIP to a NAT Gateway.

-   If you have purchased a NAT bandwidth package before January 26, 2018, you are not allowed to bind an EIP to NAT Gateway. Open a ticket to use EIP.

-   You have already created an EIP. For more information, see [Create an EIP](../../../../../intl.en-US/User Guide/Create an EIP.md#).
-   Use the [new VPC console](https://vpcnext.console.aliyun.com/nat/).

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click **More** \> **Bind Elastic IP Address** .
5.  In the displayed dialog box, complete these configurations: 
    1.  **Public IP**: Select the EIP to bind. 

        **Note:** Up to 10 EIPs can be bound to a NAT Gateway and the bandwidth of an EIP cannot exceed 200 Mbps. Open a ticket to apply for more quota.

    2.  **VSwitches**: An SNAT rule using the selected VSwitch and EIP is automatically added if you select a VSwitch. Then, the ECS instances in the specified VSwitch can access the Internet using the EIP.
6.  Repeat the previous steps to bind more EIPs.

