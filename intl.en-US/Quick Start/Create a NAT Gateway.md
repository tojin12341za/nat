# Create a NAT Gateway {#task_il1_jvy_ydb .task}

This topic describes how to create a NAT Gateway. After you create a NAT Gateway, you can configure SNAT and DNAT entries.

A VPC and a VSwitch are created. For more information, see [Create a VPC and a VSwitch](../../../../reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#section_ufw_rhv_rdb).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  On the NAT Gateways page, click **Create NAT Gateway**.
4.  On the displayed purchase page, configure the NAT Gateway and complete the payment. The following table describes the parameters. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**|Select the region where the target VPC \(to which the NAT Gateway belongs\) is located.|
    |**VPC ID**|Select the VPC for which you want to create a NAT Gateway. After the NAT Gateway is created, you cannot change the VPC. **Note:** If you cannot find the target VPC in the VPC list, troubleshoot as follows:

    -   Check whether a NAT Gateway is already configured for the VPC. A VPC can be configured with only one NAT Gateway.
    -   Check whether there is a custom route entry whose destination CIDR block is 0.0.0.0/0 in the VPC. If so, delete this custom route entry.
 |
    |**Specification**|Select a specification for the NAT Gateway. Different specifications correspond to different Max Connections and Connections Per Second \(CPS\) of the SNAT function. However, the data throughput is not affected. **Note:** The specification does not limit the number of connections and throughput of the DNAT function. For more information, see [Specifications of NAT Gateway](../../../../reseller.en-US/User Guide/Specifications of NAT Gateway.md#).

 |
    |**Billing cycle**|Select a billing cycle for the NAT Gateway.|


