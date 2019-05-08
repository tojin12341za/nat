# Manage an SNAT table {#concept_pnw_cdl_32b .concept}

The SNAT function provides an Internet proxy service for ECS instances located in a VPC that do not have public IP addresses to be permitted access to the Internet.

## SNAT entries {#section_qnw_cdl_32b .section}

The SNAT function in the NAT Gateway is abstracted as an SNAT table. You can create an SNAT entry in the SNAT table to use the SNAT function.

Each SNAT entry consists of a VSwitch and a public IP address. The VSwitch is where the ECS instance to use the SNAT function is located and the public IP address is the Elastic IP Address \(EIP\) associated with the NAT Gateway, as shown in the following table.

**Note:** If you purchased a bandwidth package before January 26, 2018, the public IP address is the IP address of the bandwidth package.

|VSwitch|Public IP address|
|:------|:----------------|
|vsw-184ipsxxx|139.224.xx.xx|
|vsw-11qht5xxx|139.224.xx.xx|

After you configure an SNAT entry, when an ESC instance in the specified VSwitch initiates an Internet access request, NAT Gateway will provide it with the Internet proxy service so that the ECS instance can use the specified public IP address to access the Internet. By default, all the ECS instances belonging to the VSwitch can use the specified public IP address to access the Internet.

**Note:** If an ECS instance is already configured with a public IP address \(such as an EIP\), the system will use the pre-configured public IP address to access the Internet and will not activate the SNAT function.

## Add an SNAT entry {#section_unw_cdl_32b .section}

To add an SNAT entry, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Find the target NAT Gateway and click its NAT Gateway ID.
5.  In the left-side navigation pane, click **SNAT Table**, and then click **Create SNAT Entry**.
6.  Configure the SNAT entry according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**VSwitch Granularity**|
    |**VSwitch**|Select the VSwitch where the ECS instances that require the Internet access are located. All ECS instances that belong to the specified VSwitch can use the specified public IP address to access the Internet. **Note:** If an ECS instance is already configured with a public IP address \(such as an EIP\), the pre-configured public IP address is used to access the Internet instead of using the SNAT proxy service.

 |
    |**VSwitch CIDR Block**|Displays the CIDR block of the selected VSwitch.|
    |**Public IP**|Select the public IP address that is used to access the Internet. **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |
    |**Entry Name**|Enter a name for the SNAT entry to be created. The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character.

 |
    |**ECS Granularity**|
    |**Available ECS Instances**|Select an ECS instance in the corresponding VPC that needs to access the Internet. The selected ECS instance will access the Internet by using the specified public IP address. Make sure that:

    -   The ECS instance is running.
    -   The ECS instance is not associated with any dedicated public IP addresses or EIPs.
 |
    |**ECS CIDR Block**|Displays the CIDR block of the selected ECS instance.|
    |**Public IP**|Select a public IP address that the ECS instance can use to access the Internet. **Note:** The public IP address that is already used for a DNAT entry cannot be used for an SNAT entry.

 |


## Edit an SNAT entry {#section_b4w_cdl_32b .section}

To edit an SNAT entry, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target NAT Gateway and click **Configure SNAT** in the **Actions** column.
5.  Click **Edit** on the right of the target SNAT entry to edit the SNAT configurations.

## Delete an SNAT entry {#section_d4w_cdl_32b .section}

To delete an SNAT entry, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Find the target NAT Gateway and click **Configure SNAT** in the **Actions** column.
5.  Click **Remove** on the right of the target SNAT entry, and then click **OK**.

