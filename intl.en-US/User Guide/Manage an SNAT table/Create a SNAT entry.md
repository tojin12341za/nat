# Create a SNAT entry {#task_491135 .task}

This topic describes how to create a SNAT entry. The SNAT function allows ECS instances that are not associated with public IP addresses in a VPC to access the Internet.

-   A NAT Gateway is created and is associated with an Elastic IP Address \(EIP\). For more information, see [Create a NAT Gateway](../reseller.en-US/Quick Start/Create a NAT Gateway.md#) and [Associate an EIP with a NAT Gateway](../reseller.en-US/Quick Start/Associate an EIP with a NAT Gateway.md#).

    **Note:** If you purchased a bandwidth package before January 26, 2018, make sure that a public IP address is available in the bandwidth package.

-   If you want to create a SNAT entry with VSwitch granularity, make sure that a VSwitch has been created in the VPC associated with the NAT Gateway. For more information, see [Create a VSwitch](../reseller.en-US/User Guide/VPC and subnets/Manage VSwitches.md#section_hd5_g5x_rdb).
-   If you want to create a SNAT entry with ECS granularity, make sure that an ECS instance has been created in the VPC associated with the NAT Gateway. For more information, see [Create an instance by using the wizard](../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  On the NAT Gateways page, find the target NAT Gateway instance and click **Configure SNAT** in the **Actions** column.
5.  On the SNAT Table page, click **Create SNAT Entry**.
6.  On the Create SNAT Entry page, configure the SNAT entry and click **OK**. The following table describes the parameters. 

    |Configuration|Description|
    |:------------|:----------|
    |**VSwitch Granularity**|
    |**VSwitch**|Select the VSwitch for which you want to create the SNAT entry in the associated VPC. All ECS instances that belong to the specified VSwitch can access the Internet through the SNAT function. **Note:** If an ECS instance is already associated with a public IP address \(for example, it is assigned a public IP address, associated with an EIP, or configured with DNAT IP mapping\), the ECS instance accesses the Internet by using the associated public IP address instead of the SNAT function of the NAT Gateway. To configure ECS instances in a VPC with the same public IP address, see [Attach an ENI to an ECS that is allocated with an public IP address](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md#), [Attach an ENI to an ECS instance associated with an EIP](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md#), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md#).

 |
    |**VSwitch CIDR Block**|The CIDR block of the selected VSwitch.|
    |**Public IP**|Select the public IP address that is used to access the Internet. You can select multiple public IP addresses to build a SNAT IP address pool. If you select multiple public IP addresses to build a SNAT IP address pool, make sure that each public IP address is added to the same shared bandwidth. For more information, see [Add EIPs to an Internet Shared Bandwidth instance](../reseller.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Add EIPs to an Internet Shared Bandwidth instance.md#).

 **Note:** You cannot select a public IP address that is already used to create a DNAT entry.

 |
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character.

 |
    |**ECS Granularity**|
    |**Available ECS Instances**|Select the ECS instance for which you want to create the SNAT entry in the associated VPC. The selected ECS instance will access the Internet by using the specified public IP address. Make sure that the following conditions are met:

    -   The ECS instance is running.
    -   The ECS instance is not associated with any public IP addresses or EIPs.
 |
    |**ECS CIDR Block**|The CIDR block of the ECS instance.|
    |**Public IP**|Select the public IP address that is used to access the Internet. You can select multiple public IP addresses to build a SNAT IP address pool. If you select multiple public IP addresses to build a SNAT IP address pool, make sure that each public IP address is added to the same shared bandwidth. For more information, see [Add EIPs to an Internet Shared Bandwidth instance](../reseller.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Add EIPs to an Internet Shared Bandwidth instance.md#).

 **Note:** You cannot select a public IP address that is already used to create a DNAT entry.

 |
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character.

 |


