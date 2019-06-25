# Attach an ENI to an ECS instance configured with DNAT IP mapping {#concept_711329 .concept}

This topic describes how to attach an ENI to an ECS instance configured with DNAT IP mapping. After you attach an ENI to an ECS instance configured with DNAT IP mapping, you can uniformly manage public IP addresses of ECS instances in a VPC.

## Prerequisites {#section_guz_qq7_inj .section}

The VPC to which the ECS instance configured with DNAT IP mapping is configure with the SNAT function. For more information, see [Create an SNAT entry](../reseller.en-US/Quick Start/Create an SNAT entry.md#).

## Background information {#section_uvy_nls_sa5 .section}

NAT Gateway supports SNAT, which is a function that allows ECS instances without a public IP address in a VPC to access the Internet. If an ECS instance in a VPC is configured with DNAT IP mapping \(full port mapping\), the ECS instance accesses the Internet through the public IP address in the corresponding DNAT entry, while other ECS instances in the VPC access the Internet through the SNAT function of NAT Gateway. Therefore, ECS instances in the VPC use different IP addresses to access the Internet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570564/156144625749565_en-US.png)

You can attach an ENI to the ECS instance to uniformly manage the public IP addresses of ECS instances in the VPC.

As shown in the following figure, you can attach an ENI to the ECS instance, remove the corresponding DNAT entry in the NAT Gateway, create a new DNAT entry, and map a public IP address on the NAT Gateway to the ENI, so that traffic from the Internet accesses the ECS instance through the ENI, and the ECS instance accesses the Internet through NAT Gateway.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144625749551_en-US.png)

## Step 1: Create an ENI {#section_on9_ddc_6rg .section}

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

## Step 2: Attach the ENI to the ECS instance {#section_5b2_9sh_9rm .section}

To attach the ENI to the ECS instance, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.aliyun.com/login-required#/ecs).
2.  In the left-side navigation pane, click **Network and Security** \> **ENI**.
3.  Select the target region.
4.  On the Network Interfaces page, find the target ENI, and click **Bind to Instance** in the **Actions** column.
5.  In the displayed dialog box, select the ECS instance to attach and click **OK**.

## Step 3: Remove the DNAT entry {#section_miz_l1c_xmx .section}

To remove the corresponding DNAT entry in the NAT Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the target region.
4.  On the NAT Gateways page, find the target NAT Gateway and click **Configure DNAT** in the **Actions** column.
5.  On the DNAT Entry List page, find the target DNAT entry and click **Remove** in the **Actions** column.
6.  In the displayed dialog box, click **OK**.

## Step 4: Create a DNAT entry {#section_9gh_p20_u4c .section}

To create a DNAT entry and map a public IP address in the NAT Gateway to the ENI, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  On the NAT Gateways page, find the target NAT Gateway instance and click **Configure DNAT** in the **Actions** column.
4.  On the DNAT Entry List page, click **Create DNAT Entry**.
5.  On the Create DNAT Entry page, configure the DNAT entry according to the following information and click **OK**.
    -    **Public IP**: Select an available public IP address. An IP address that is already being used in an SNAT entry cannot be selected.
    -    **Private IP address**: Select the ENI instance.
    -    **Port Settings**: Select All Ports.
    -    **Entry Name**: Enter the name of the DNAT entry.

## Step 5: Test the network connectivity {#section_v6f_yti_doa .section}

Follow these steps to test whether the ECS instance can be accessed from the Internet through the EIP associated with the ENI. In this tutorial, a Linux instance is accessed from a remote Linux client.

**Note:** The security group rules of the Linux instance must allow access from the SSH \(22\) port. For more information, see [../../SP\_2/DNECS19100344/EN-US\_TP\_9718.md\#](../../reseller.en-US/Security/Security groups/Add security group rules.md#).

1.  Log on to the Linux client.
2.  Run the `ssh root@ public IP address` command and enter the logon password of the Linux instance to check if the remote access is successful.

    If Welcome to Alibaba Cl oud Elastic Compute Service! is displayed,it means that the connection has been established.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144625749595_en-US.png)


Follow these steps to test if the ECS instance can access the Internet through the SNAT function of NAT Gateway. In this tutorial, the public IP address used is checked.

1.  Log on to the ECS instance.
2.  Run the `curl https://myip.ipip.net` to view the public IP address.

    If the public IP address is the same as the IP address in the SNAT entry of the NAT Gateway, it means that the ECS instance accesses the Internet through the SNAT function of NAT Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144625849596_en-US.png)


