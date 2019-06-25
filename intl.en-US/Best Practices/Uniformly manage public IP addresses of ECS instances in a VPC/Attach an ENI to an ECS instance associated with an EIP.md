# Attach an ENI to an ECS instance associated with an EIP {#concept_711105 .concept}

The topic describes how to attach an ENI to an ECS instance associated with an EIP. When you attach an ENI to an ECS instance, you can uniformly manage public IP addresses of the ECS instances in a VPC.

## Prerequisites {#section_4wd_95d_1u6 .section}

The VPC to which the ECS instance associated with an EIP belongs is configured with the SNAT function. For more information, see [Create an SNAT entry](../reseller.en-US/Quick Start/Create an SNAT entry.md#).

## Background Information {#section_5fr_xw0_tg7 .section}

NAT Gateway supports SNAT, which allows an ECS instance without a public IP address in a VPC to access the Internet. If an ECS instance in a VPC is configured with an EIP, the ECS instance accesses the Internet through the EIP, while other ECS instances in the VPC access the Internet through the SNAT function of NAT Gateway. Therefore, ECS instances in the VPC use different IP addresses to access the Internet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570281/156144622949564_en-US.png)

You can attach an ENI to the ECS instance to uniformly manage the public IP addresses of the ECS instances in a VPC.

As shown in the following figure, you can attach an ENI to the ECS instance and associate the EIP with the ENI, so that traffic from the Internet accesses the ECS instance through the ENI, and the ECS instance accesses the Internet through NAT Gateway.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144622949551_en-US.png)

## Step 1: Create an ENI {#section_o0f_8z1_yy6 .section}

To create an ENI for an ECS instance, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.aliyun.com/login-required#/ecs).
2.  In the left-side navigation pane, click **Network and Security** \> **ENI**.
3.  Select the target region.

    **Note:** The ENI and the ECS instance must be in the same region.

4.  On the Network Interfaces page, click **Create ENI**.
5.  On the Create ENI page, configure the ENI according to the following information and click **OK**.
    -    **Network Interface Name**: Enter the name of the ENI.
    -    **VPC**: Select the VPC to which the ECS instance belongs.
    -    **VSwitch**: Select the VSwitch of the zone to which the ECS instance belongs.
    -    **Primary Private IP** \(optional\): Enter the primary private IPv4 address of the ENI. The IPv4 address must be an idle address in the CIDR block of the specified VSwitch. If you do not specify one, an idle private IPv4 address is automatically assigned to your ENI after the ENI is created.
    -    **Security Group**: Select a security group of the VPC.
    -    **Description** \(optional\): Enter a description for the ENI.

## Step 2: Attach the ENI to the ECS instance {#section_wim_o2h_o37 .section}

To attach the ENI to the ECS instance, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.aliyun.com/login-required#/ecs).
2.  In the left-side navigation pane, click **Network and Security** \> **ENI**.
3.  Select the target region.
4.  On the Network Interfaces page, find the target ENI, and click **Bind to Instance** in the **Actions** column.
5.  In the displayed dialog box, select the ECS instance to attach and click **OK**.

## Step 3: Disassociate the EIP from the ECS instance {#section_4xl_wtb_54i .section}

To disassociate the EIP from the ECS instance, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region of the target EIP.
4.  On the Elastic IP Addresses page, find the target EIP and click **Unbind** in the **Actions** column.
5.  In the displayed dialog box, click **OK**.

## Step 4: Associate the EIP with the ENI {#section_n7o_cgd_03c .section}

To associate the EIP with the ENI, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region of the target EIP.
4.  On the Elastic IP Addresses page, find the target EIP and click **Bind** in the **Actions** column.
5.  On the Bind Elastic IP Address page, associate the EIP with the ENI according to the following information and click **OK**.
    -    **IP Address**: Displays the EIP.
    -    **Instance Type**: Select Secondary ENI.
    -    **Resource Group** \(optional\): Select the resource group to which the EIP belongs.
    -    **Mode** \(optional\): Select the NAT mode.
    -    **Secondary ENI**: Select the ENI to be associated.

## Step 5: Test the network connectivity {#section_eb3_nk5_90p .section}

Follow these steps to test whether the ECS instance can be accessed from the Internet through the EIP associated with the ENI. In this tutorial, a Linux instance is accessed from a remote Linux client.

**Note:** The security group rules of the Linux instance must allow access from the SSH \(22\) port. For more information, see [../../SP\_2/DNECS19100344/EN-US\_TP\_9718.md\#](../../reseller.en-US/Security/Security groups/Add security group rules.md#).

1.  Log on to the Linux client.
2.  Run the `ssh root@ public IP address` command and enter the logon password of the Linux instance to check if the remote access is successful.

    If Welcome to Alibaba Cl oud Elastic Compute Service! is displayed,it means that the connection has been established.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144623049595_en-US.png)


Follow these steps to test if the ECS instance can access the Internet through the SNAT function of NAT Gateway. In this tutorial, the public IP address used is checked.

1.  Log on to the ECS instance.
2.  Run the `curl https://myip.ipip.net` to view the public IP address.

    If the public IP address is the same as the IP address in the SNAT entry of the NAT Gateway, it means that the ECS instance accesses the Internet through the SNAT function of NAT Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144623049596_en-US.png)


