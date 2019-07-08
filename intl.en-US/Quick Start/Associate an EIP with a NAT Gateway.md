# Associate an EIP with a NAT Gateway {#task_o3q_3xy_ydb .task}

This topic describes how to associate an Elastic IP Address \(EIP\) with a NAT Gateway. A NAT Gateway can work normally only after it is associated with a public IP address. After you associate an EIP with a NAT Gateway, you can use the EIP to configure SNAT entries.

Before you associate an EIP with a NAT Gateway, make sure that the following conditions are met:

-   Your NAT bandwidth package was purchased after January 26, 2018. If you purchased a package before January 26, 2018, you must open a ticket before you can associate an EIP with your NAT Gateway.

-   A NAT Gateway and an EIP are created. For more information, see [Create a NAT Gateway](reseller.en-US/Quick Start/Create a NAT Gateway.md#) and [Create an EIP](../../../../reseller.en-US/User Guide/Create an EIP/Create an EIP.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target NAT Gateway and choose **More** \> **Bind Elastic IP Address** in the **Actions** column.
5.  On the Bind Elastic IP Address page, complete the following configurations, and then click **OK**. 

    |Configuration|Description|
    |-------------|-----------|
    |**Select from EIP list**|
    |**Usable EIP list**|Select an EIP that is used to access the Internet.|
    |**VSwitch**|Select the VSwitch to which you want to add SNAT entries. The system automatically adds SNAT entries so that Alibaba Cloud services connected to this VSwitch can access the Internet. Alternatively, you can skip this step and add SNAT entries after you associate an EIP with a NAT Gateway. For more information, see [Create a SNAT entry](reseller.en-US/Quick Start/Create a SNAT entry.md#).

 **Note:** This option is displayed only for NAT Gateways that are not associated with an EIP.

 |
    |**Allocate one EIP and bind it to NAT Gateway**|
    |**Buy EIP**|Displays the number of EIPs to be purchased. The default value is 1 and cannot be modified. The system automatically creates an EIP billed by traffic and associate it with the NAT Gateway.

 |

    **Note:** One NAT Gateway can be associated with up to 20 EIPs, including up to 10 EIPs billed by traffic. The peak bandwidth of each EIP billed by traffic cannot exceed 200 Mbps. However, you can open a ticket to increase the quota of EIPs that one NAT Gateway can be associated with.


