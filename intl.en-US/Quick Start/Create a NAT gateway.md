# Create a NAT gateway {#task_il1_jvy_ydb .task}

You must create a NAT Gateway before configuring SNAT and DNAT entries.

A VPC is already created. For more information [Create a VPC and a VSwitch](../../../../../reseller.en-US/User Guide/Manage a VPC.md#section_ufw_rhv_rdb).

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **NAT Gateways**. 
3.   Click **Create NAT Gateway**. 
4.  Configure the NAT Gateway according to the following information and complete the payment. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**|Select the region of the NAT Gateway. Make sure the regions of the NAT Gateway and VPC are the same.|
    |**VPC ID**| Select the VPC for which the NAT Gateway is created. After the gateway is created, you cannot change the VPC.

 If you cannot find the expected VPC in the VPC list, troubleshoot as follows:

     -   Check whether the VPC already has a NAT gateway configured.  A VPC can be configured with only one NAT gateway.

    -   Check whether a custom route entry, whose destination CIDR block is 0.0.0.0/0, already exists in the VPC.  If so, delete this custom route entry.

 |
    |**Specifications**| Select a specification for the NAT Gateway. The specification affects the maximum number of connections and the number of new connections allowed per second for the SNAT proxy service, but does not affect data throughput.

 **Note:** The specification has no impact on the number of connections and throughput of the DNAT function. For more information, see [Specifications of NAT Gateway](../reseller.en-US/User Guide/Specifications of NAT Gateway.md#).

 |
    |**Billing Cycle**|Display the billing cycle for NAT Gateway.|


