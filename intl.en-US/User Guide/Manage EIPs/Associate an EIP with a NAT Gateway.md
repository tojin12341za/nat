# Associate an EIP with a NAT Gateway {#task_491164 .task}

This topic describes how to associate an Elastic IP Address \(EIP\) with a NAT Gateway. A NAT Gateway can work normally only after it is associated with a public IP address. After you create a NAT Gateway, you can associate an EIP with the NAT Gateway.

Before you associate an EIP with a NAT Gateway, make sure that the following conditions are met.

-   If you have purchased a NAT bandwidth package before January 26, 2018, you are not allowed to associate an EIP with a NAT Gateway. Open a ticket to use EIP.

-   A NAT Gateway and an EIP are created. For more information, see [Create a NAT Gateway](../reseller.en-US/Quick Start/Create a NAT Gateway.md#) and [Create an EIP](../reseller.en-US/User Guide/Create an EIP/Create an EIP.md#).

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **NAT Gateways**. 
3.   Select the region of the NAT Gateway. 
4.   Find the target NAT Gateway and choose **More** \> **Bind Elastic IP Address** in the **Actions** column. 
5.   On the Bind Elastic IP Address page, complete the following configurations, and then click **OK**. 

    |Configuration|Description|
    |-------------|-----------|
    | **Select from EIP list** |You can select an EIP from the EIP list and associate it with the NAT Gateway.|
    | **Allocate one EIP and bind it to NAT Gateway** |The system creates a Pay-As-You-Go EIP billed based on traffic for you and associate it with the NAT Gateway.|

    **Note:** One NAT Gateway can be associated with up to 20 EIPs \(and can be associated with up to 10 EIPs billed based on traffic. The peak bandwidth of each EIP billed on traffic cannot exceed 200 Mbps\). To increase the quota, open a ticket.


