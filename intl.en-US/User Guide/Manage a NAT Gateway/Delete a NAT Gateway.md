# Delete a NAT Gateway {#task_491107 .task}

This topic describes how to delete a NAT Gateway.

Before you delete a NAT Gateway, make sure that the following conditions are met:

-   The NAT Gateway is not associated with an EIP. For more information, see [Disassociate an EIP from a NAT Gateway](reseller.en-US/User Guide/Manage EIPs/Disassociate an EIP from a NAT Gateway.md#).
-   The DNAT table does not contain any DNAT entry. For more information, see [Delete a DNAT entry](reseller.en-US/User Guide/Manage a DNAT table/Delete a DNAT entry.md#).
-   The SNAT table does not contain any SNAT entry. For more information, see [Delete an SNAT entry](reseller.en-US/User Guide/Manage an SNAT table/Delete an SNAT entry.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.   On the NAT Gateways page, find the target NAT Gateway and click **More** \> **Delete** in the **Actions** column. 
5.   In the displayed dialog box, click **OK**. 

    **Note:** You can also click **Delete \(Delete NAT gateway and resources\)** to forcibly delete the NAT Gateway. After the NAT Gateway is deleted, DNAT and SNAT entries in the NAT Gateway are deleted and EIPs are disassociated automatically.


