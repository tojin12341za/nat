# Manage an SNAT table {#concept_pnw_cdl_32b .concept}

The SNAT function provides the Internet proxy service for the ECS instances of the VPC network. Therefore, the ECS instances can access the Internet.

## SNAT entries {#section_qnw_cdl_32b .section}

The SNAT function in the NAT Gateway is abstracted as an SNAT table. You can create an SNAT entry to use the SNAT function.

Each SNAT entry consists of a VSwitch and a public IP. The VSwitch is where the ECS instance to use the SNAT function is located and the public IP is the EIP bound to the NAT Gateway, as shown in the following table.

**Note:** If your account has purchased a bandwidth package before January 26, 2018, the public IP is the IP of the bandwidth package.

|VSwitch|Public IP|
|:------|:--------|
|vsw-184ipsxxx|139.224.xx.xx|
|vsw-11qht5xxx|139.224.xx.xx|

After configuring an SNAT entry, when an ESC instance in the specified VSwitch initiates an Internet access request, NAT Gateway will provide it with the Internet proxy service and then the ECS instance can use the specified public IP to access the Internet. By default, all the ECS instances belonging to the VSwitch can use the specified public IP to access the Internet.

**Note:**  If an ECS instance already has a public IP \(such as an EIP\), the system will use the pre-configured public IP to access the Internet and will not activate the SNAT function.

## Add an SNAT entry {#section_unw_cdl_32b .section}

To add an SNAT entry, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target the NAT Gateway.
5.  In the left-side navigation pane, click **SNAT Table**, and then click **Create SNAT Entry**.
6.  Configure the SNAT entry according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**VSwitch**| Select the VSwitch where the ECS instances that require the Internet access are located. All ECS instances in the specified VSwitch can use the specified public IP to access the Internet.

 **Note:** If an ECS instance has already configured a public IP \(such as an EIP\), the pre-configured public IP is used to access the Internet instead of using the SNAT proxy service.

 |
    |**VSwitch CIDR block**|Display the CIDR block of the selected VSwitch.|
    |**Internet IP Address**| Select public IP that is used to access the Internet.

 **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |


## Edit an SNAT entry {#section_b4w_cdl_32b .section}

To edit an SNAT entry, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the **Configure SNAT** option of the target NAT Gateway.
5.  Click **Edit** of the target SNAT entry to edit the SNAT configurations.

## Delete an SNAT entry {#section_d4w_cdl_32b .section}

To delete an SNAT entry, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway, and then click the ID of the target NAT Gateway.
4.  Click the **Configure SNAT** option of the target NAT Gateway.
5.  Click **Remove** of the target SNAT entry, and then click **OK**.

