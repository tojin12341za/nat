# Manage a NAT Gateway {#concept_ehq_cbz_ydb .concept}

A NAT Gateway instance is a running NAT Gateway service. You must create a NAT Gateway instance before configuring SNAT and DNAT entries.

## Create a NAT Gateway instance {#section_iml_hbz_ydb .section}

To create a NAT Gateway instance, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Click **Create NAT Gateway**.
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

 **Note:** The specification has no impact on the number of connections and throughput of the DNAT function. For more information, see [Specifications of NAT Gateway](intl.en-US/User Guide/Specifications of NAT Gateway.md#).

 |
    |**Billing Cycle**|Display the billing cycle for NAT Gateway.|


## Change a specification {#section_jml_hbz_ydb .section}

You can change the specification of a NAT Gateway according to your business needs. The specification of the NAT Gateway only affects the performance of SNAT and has no effect on the DNAT performance.

To change the specification for a NAT Gateway, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the instance ID of the target NAT Gateway.
5.  On the details page, click **Change Specification**.
6.  In the **Configuration upgrade** area, select a new specification and then click **Activate**.

## Edit a NAT Gateway {#section_mml_hbz_ydb .section}

To edit a NAT Gateway, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  On the NAT Gateway Details page, click **Edit** next to the name and description. Enter a name or description and then click **OK**.

## Delete a NAT Gateway {#section_rf4_2cz_ydb .section}

To delete a NAT Gateway, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Find the target NAT Gateway, and then click **Delete**. In the displayed dialog box, click **OK**.

    **Note:** You can also click **Delete \(Delete NAT gateway and resources\)** to delete the NAT Gateway by force. After the NAT Gateway is deleted, the EIP is unbound automatically.


