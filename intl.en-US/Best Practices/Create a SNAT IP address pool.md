# Create a SNAT IP address pool {#concept_264331 .concept}

This topic describes how to create a SNAT IP address pool by adding multiple EIPs to the SNAT IP address pool. After you create a SNAT IP address pool, ECS instances in a VPC can access the Internet by using the EIPs in the SNAT address pool.

## Prerequisites {#section_au7_r96_xlc .section}

-   A VPC and a VSwitch are created. For more information, see [Create a VPC and a VSwitch](../../../../reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#section_ufw_rhv_rdb).
-   An EIP is created. For more information, see [Create an EIP](../../../../reseller.en-US/User Guide/Create an EIP/Create an EIP.md#).

## Background information {#section_doq_73k_duj .section}

A NAT Gateway is an enterprise-class VPC-based Internet gateway that provides the SNAT function. It enables ECS instances without public IP addresses in a VPC to access the Internet. If you configure only one EIP for the specified VSwitch or ECS instance when you create a SNAT entry, this EIP cannot process huge traffic when the ECS instance initiates a large number of Internet access requests.

You can add multiple EIPs to a SNAT address pool. When an ECS instance in a VPC initiates an access request, the ECS instance randomly accesses the Internet by using an EIP in the SNAT address pool.

![SNAT IP address pool](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156375765647136_en-US.png)

## Step 1: Create a NAT Gateway {#section_kaj_h2e_nto .section}

To create a NAT Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  On the NAT Gateways page, click **Create NAT Gateway**.
4.  On the displayed purchase page, configure the NAT Gateway and complete the payment. The following table describes the parameters.
    -   **Region**: Select the region where the target VPC \(to which the NAT Gateway belongs\) is located.
    -   **VPC ID**: Select the VPC for which you want to create a NAT Gateway. After the NAT Gateway is created, you cannot change the VPC.

        **Note:** If you cannot find the target VPC in the VPC list, troubleshoot as follows:

        -   Check whether a NAT Gateway is already configured for the VPC. A VPC can be configured with only one NAT Gateway.
        -   Check whether there is a custom route entry whose destination CIDR block is 0.0.0.0/0 in the VPC. If so, delete this custom route entry.
    -   **Specification**: Select the specification of the NAT Gateway. Different specifications correspond to different Max Connections and Connections Per Second \(CPS\) of the SNAT function. However, the data throughput is not affected.

        **Note:** The specification does not limit the number of connections and throughput of the DNAT function. For more information, see [Specifications of NAT Gateway](../../../../reseller.en-US/User Guide/Specifications of NAT Gateway.md#).

    -   **Billing Cycle**: Select the billing cycle of the NAT Gateway.

## Step 2: Associate an EIP with the NAT Gateway {#section_7mo_onm_20l .section}

To associate EIPs with the NAT Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target NAT Gateway and choose **More** \> **Bind Elastic IP Address** in the **Actions** column.
5.  On the Bind Elastic IP Address page, complete the following configurations, and then click **OK**.

    -   **Select from EIP list**: Select an EIP from the existing EIP list and associate the EIP with the NAT Gateway.
    -   **Allocate one EIP and bind it to NAT Gateway**: The system automatically creates an EIP billed by traffic and associate the EIP with the NAT Gateway.
    **Note:** One NAT Gateway can be associated with up to 20 EIPs, including up to 10 EIPs billed by traffic. The peak bandwidth of each EIP billed by traffic cannot exceed 200 Mbps. However, you can open a ticket to increase the quota of EIPs that one NAT Gateway can be associated with.

6.  Repeat the preceding steps to associate more EIPs with the NAT Gateway.

## Step 3: Add an EIP to a shared bandwidth {#section_nes_2cn_dhg .section}

To add an EIP to a shared bandwidth, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region to which the target EIP belongs.
4.  On the Elastic IP Addresses page, find the target EIP, and then choose **More** \> **Add to Shared Bandwidth Package** in the **Actions** column.
5.  Select the target Internet Shared Bandwidth, and then click **OK**.

## Step 4: Create a SNAT entry {#section_8i2_1th_793 .section}

To create a SNAT entry and add multiple EIPs to a SNAT address pool, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  On the NAT Gateways page, find the target NAT Gateway instance and click **Configure SNAT** in the **Actions** column.
5.  On the SNAT Table page, click **Create SNAT Entry**.
6.  On the Create SNAT Entry page, configure the SNAT entry and click **OK**. The following table describes the parameters.

    On the **VSwitch Granularity** tab page, complete the following settings:

    -   **VSwitch**: Select a VSwitch in the VPC. All ECS instances that belong to the specified VSwitch can access the Internet through the SNAT function.
    -   **VSwitch CIDR Block**: the CIDR block of the VSwitch.
    -   **Public IP**: Select the public IP address that is used to access the Internet. You can select multiple public IP addresses to build a SNAT IP address pool.
    -   **Entry Name**: Enter the name of the SNAT entry.
    On the **ECS Granularity** tab page, complete the following settings:

    -   **Available ECS Instances**: Select an ECS instance in the VPC.
    -   **ECS CIDR Block**: the CIDR block of the ECS instance.
    -   **Public IP**: Select the public IP address that is used to access the Internet. You can select multiple public IP addresses to build a SNAT IP address pool.
    -   **Entry Name**: Enter the name of the SNAT entry.

## Step 5: Test access to the Internet {#section_xes_80x_bgv .section}

Log on to two ECS instances configured with SNAT rules to view the source IP addresses used to access the Internet.

![View the source IP address of ECS1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156375765647157_en-US.png)

![View the source IP address of ECS2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156375765647158_en-US.png)

