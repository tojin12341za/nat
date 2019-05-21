# Create an SNAT IP address pool {#concept_264331 .concept}

When you create SNAT entries, you can add multiple EIPs to an SNAT address pool. In this way, ECS instances of the VPC network can access the Internet by using the EIPs in the SNAT address pool.

## Prerequisites {#section_au7_r96_xlc .section}

-   A VPC and a VSwitch are created. For more information, see [Create a VPC and a VSwitch](../../../../../reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#section_ufw_rhv_rdb).
-   An EIP to be added to the SNAT address pool is created. For more information, see [Create an EIP](../../../../../reseller.en-US/User Guide/Create an EIP.md#).

## Background information {#section_doq_73k_duj .section}

NAT Gateway is an enterprise-class VPC-based Internet gateway that provides the SNAT function. It enables ECS instances in a VPC that do not have public IP addresses to access the Internet. When you create an SNAT entry in the NAT console, you can configure only one public IP address \(default\) for the VSwitch. However, a single EIP cannot handle traffic when access requests to an ECS instance spike.

You can call the CreateSnatEntry action to create SNAT entries to add multiple EIPs to an SNAT address pool. In this case, you can call the CreateSnatEntry action to create SNAT entries and add multiple EIPs to an address pool. Then, ECS instances of the VPC network access the Internet by randomly using EIPs in the SNAT address pool.

**Note:** If you purchased a NAT bandwidth package before January 26, 2018 and want to create an SNAT IP address pool, see [Create an SNAT IP address pool](https://yq.aliyun.com/articles/533821).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/155840074547136_en-US.png)

## Step 1: Create a NAT Gateway {#section_kaj_h2e_nto .section}

To create a NAT Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Click **Create NAT Gateway**.
4.  Configure the NAT Gateway according to the following information and complete the payment.

    |Configuration|Description|
    |:------------|:----------|
    |**Region**|Select the region to which the NAT Gateway will be located. Make sure the regions of the NAT Gateway and VPC are the same.|
    |**VPC ID**| Select the VPC for which the NAT Gateway is created. After the gateway is created, you cannot change the VPC.

 If you cannot find the target VPC in the VPC list, troubleshoot as follows:

     -   Check whether the VPC already has a NAT Gateway configured. A VPC can be configured with only one NAT Gateway.

    -   Check whether a custom route entry, whose destination CIDR block is 0.0.0.0/0, already exists in the VPC. If so, delete this custom route entry.

 |
    |**Specifications**| Select a specification for the NAT Gateway. The specification affects the maximum number of connections and the number of new connections allowed per second for the SNAT proxy service, but does not affect data throughput.

 **Note:** The specification does not limit the number of connections and throughput of the DNAT function. For more information, see [Specifications of NAT Gateway](../reseller.en-US/User Guide/Specifications of NAT Gateway.md#).

 |
    |**Billing Cycle**|Select a billing cycle for the NAT Gateway.|


## Step 2: Associate EIPs {#section_7mo_onm_20l .section}

To associate an EIP to a NAT Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Find the target NAT Gateway and choose **More** \> **Bind Elastic IP Address** in the **Actions** column.
5.  In the displayed dialog box, complete the following configurations:
    1.  **Public IP**: Select the EIP to be associated with the NAT Gateway.
    2.  **VSwitches \(Optional\)**: If you select a VSwitch, the system automatically adds an SNAT rule so that cloud products under the VSwitch can access the Internet through the selected EIP.
6.  To associate more EIPs with the NAT Gateway, repeat the previous steps.

## Step 3: Add the EIPs to an Internet Shared Bandwidth {#section_nes_2cn_dhg .section}

To add an EIP to an Internet Shared Bandwidth, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region to which the target EIP belongs.
4.  On the Elastic IP Addresses page, find the target EIP, and click **More** \> **Add to Shared Bandwidth Package** in the **Actions** column.
5.  Select the target Internet Shared Bandwidth instance and then click **OK**.

## Step 4: Create SNAT entries {#section_b2u_tma_3wd .section}

To create SNAT entries, follow these steps:

1.  Log on to the [OpenAPI Explorer](https://api.aliyun.com).
2.  In the left-side navigation pane, click **Virtual Private Cloud**.
3.  In the search box, enter **CreateSnatEntry** and click **CreateSnatEntry**.
4.  Configure the CreateSnatEntry parameters according to the following information, and then click **Submit Request**.

    -   **RegionId**: The ID of the region to which the NAT Gateway belongs.
    -   **SnatTableId**: The ID of the SNAT table.
    -   **SnatIp**: EIPs added to the SNAT address pool. Separate multiple IP addresses with commas.
    -   **SourceVSwitchId** \(optional\): the ID of the VSwitch to access the Internet.
    -   **SourceCIDR** \(optional\): The CIDR block of the VSwitch.
    -   **SnatEntryName** \(optional\): the name of the SNAT entry.
    For more information, see [../../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2551.md\#](../../../../../reseller.en-US/API reference/NAT Gateway/CreateSnatEntry.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/155840074547549_en-US.png)


If you have created an SNAT entry, you can call the ModifySnatEntry API to modify the SNAT entry. The ModifySnatEntry parameters are as follows:

-   **RegionId**: The ID of the region to which the NAT Gateway belongs.
-   **SnatTableId**: The ID of the SNAT table.
-   **SnatEntryId**: The ID of the SNAT entry.
-   **SnatIp**: EIPs added to the SNAT address pool. Separate multiple IP addresses with commas.
-   **SnatEntryName**: The name of the SNAT entry.

For more information, see [../../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2553.md\#](../../../../../reseller.en-US/API reference/NAT Gateway/ModifySnatEntry.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/155840074547556_en-US.png)

## Step 5: Test access to the Internet {#section_xes_80x_bgv .section}

Log on to two ECS instances under the VSwitch configured with SNAT rules to view the source IP addresses used to access the Internet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/155840074547157_en-US.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/155840074647158_en-US.png)

