# Manage NAT bandwidth packages {#concept_nyn_15c_zdb .concept}

After creating a NAT Gateway, you must first create a shared bandwidth package to configure SNAT and DNAT entries. A shared bandwidth package consists of multiple public IPs and a public network bandwidth.

**Note:** EIP has supported binding NAT Gateway. Open a ticket to use EIP.

## Edit shared bandwidth package {#section_jdc_g5c_zdb .section}

To edit a shared bandwidth package, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  In the left-side navigation pane, click **Shared Bandwidth Package**.
6.  In the Basic Info area, click **Edit** to enter a name and description.
7.  In the displayed dialog, enter a name and description, and then click **Confirm**.

## Add and remove public IPs {#section_mjd_q5c_zdb .section}

To add or remove public IP, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  In the left-side navigation pane, click **Shared Bandwidth Package**.
6.  In the Public IP List area, click **Add Public** to add more IPs. 
7.  In the Public IP List area, click **Release** to delete a public IP.

    **Note:** If the IP is used in an SNAT entry or a DNAT entry, delete the entry first.


## Change bandwidth {#section_z2t_w5c_zdb .section}

To change the bandwidth, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  In the Billing Info area, click **Modify Bandwidth**.
6.  In the Change configuration area, select a bandwidth and click **Activate**.

## Delete a bandwidth package {#section_nv2_dvc_zdb .section}

To delete a bandwidth package, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  In the left-side navigation pane, click **Shared Bandwidth Package**.
6.  Click **Delete** on the shared bandwidth package pane.
7.  In the displayed dialog, click **Confirm**.

