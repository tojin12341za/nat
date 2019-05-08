# Associate and disassociate EIPs {#concept_uy3_f2z_ydb .concept}

After you create a NAT Gateway, you must configure public IP addresses for the NAT Gateway. To do so, you can associate one or more Elastic IP Addresses \(EIPs\) with the NAT Gateway.

**Note:** 

If you purchased a NAT bandwidth package for your account before January 26, 2018, you cannot associate EIPs with the NAT Gateway. If you want to associate EIPs with the NAT Gateway, open a ticket.

## Associate an EIP with a NAT Gateway {#section_zx4_l2z_ydb .section}

**Note:** Make sure that you have created a NAT Gateway and an EIP.

To associate an EIP with a NAT Gateway, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Find the target NAT Gateway and choose **More** \> **Bind Elastic IP Address** in the **Actions** column.
5.  In the displayed dialog box, complete the following configurations:
    1.  **Public IP**: Select the EIP to be associated with the NAT Gateway.
    2.  **VSwitches \(Optional\)**: If you select a VSwitch, the system automatically adds an SNAT rule so that cloud products under the VSwitch can access the Internet through the selected EIP.
6.  To associate more EIPs with the NAT Gateway, repeat the previous steps.

## Disassociate an EIP from a NAT Gateway {#section_gy4_l2z_ydb .section}

**Note:** Make sure the EIP to be disassociated is not being used by any SNAT entries or DNAT entries.

To disassociate an EIP, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Find the target NAT Gateway and choose **More** \> **Unbind Elastic IP Address**.
5.  In the displayed dialog box, select the target EIP and click **OK**.

