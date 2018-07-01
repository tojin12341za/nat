# Bind and unbind EIPs {#concept_uy3_f2z_ydb .concept}

After creating a NAT Gateway, you must configure public IPs for the NAT Gateway to use. You bind one or more EIPs to a NAT Gateway as the public IPs to use.

**Note:** 

If you have purchased a NAT bandwidth package before January 26, 2018, you cannot bind an EIP to a NAT Gateway. Open a ticket if you want to bind EIP to the NAT Gateway.

## Bind an EIP {#section_zx4_l2z_ydb .section}

Make sure that you have created a NAT Gateway and an EIP.

To bind an EIP to a NAT Gateway, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target the NAT Gateway.
5.  Click **More** \> **Bind Elastic IP Address**.
6.  In the displayed dialog box, complete these configurations:
    1.  **Public IP**: Select the EIP to bind.

         

    2.  **VSwitches \(Optional\)**: If you select a VSwitch, the system automatically add an SNAT rule so that cloud products under the VSwitch can access the Internet through EIP.
7.  Repeat the previous steps to bind more EIPs.

## Unbind an EIP {#section_gy4_l2z_ydb .section}

Make sure the EIP to unbind is not used by any SNAT entries or DNAT entries.

To unbind an EIP, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target the NAT Gateway.
5.  Click **More** \> **Unbind Elastic IP Address**.
6.  In the displayed dialog box, select an EIP and click **OK**.

