# Manage a DNAT table {#concept_czl_mcz_ydb .concept}

You can use the DNAT function to map a public IP to a private IP of an ECS instance in the VPC network. Then, the ECS instance with the specified public IP can provide public services.

## DNAT entries {#section_gsb_pcz_ydb .section}

The DNAT function in the NAT gateway is abstracted as a DNAT table. You can create a DNAT entry to use the DNAT function.

A DNAT entry consists of public IP, public port, private IP, private port, and protocol. The public IP is the bound EIP whereas the private IP is the private IP address of the ECS instance. After configuring a DNAT entry, the data packet received from the specified public IP will be forwarded to the ECS instance according to the mapping rule.

**Note:** If your account has purchased a bandwidth package before January 26, 2018, the public IP is the IP of the bandwidth package.

## Port mapping and IP mapping {#section_mkg_wcz_ydb .section}

The DNAT function includes port mapping and IP mapping:

-   Port mapping

    With port mapping, the NAT Gateway will forward requests from specified protocol and port to the selected ECS instance of the specified port in the VPC. Such as the Entry 1 and Entry 2 in the following table.

-   IP mapping

    With IP mapping, the NAT Gateway will forward requests from the specified IP to the selected ECS instances in the VPC, like binding an EIP to the ECS instance. Any request to access the public IP is forwarded to the target ECS instance. Such as the Entry 3 in the following table.

    |DNAT entry|Public IP|Public port|Private IP|Private port|Protocol|
    |:---------|:--------|:----------|:---------|:-----------|:-------|
    |Entry 1|139.224.xx.xx|80|192.168.x.x|80|TCP|
    |Entry 2|139.224.xx.xx|8080|192.168.x.x|8000|UDP|
    |Entry 3|139.224.xx.xx|Any|192.168.x.x|Any|Any|


## Add a DNAT entry {#section_dv2_bdz_ydb .section}

To add a DNAT entry, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the ID of the target NAT Gateway.
5.  In the left-side navigation pane, click **DNAT Table**, and then click **Create DNAT Entry**.
6.  Configure the DNAT entry according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |**Public IP**| Select a public IP.

 **Note:** The IP that is already being used in an SNAT entry cannot be selected.

 |
    |**Private IP**| Select the private IP of the ECS instance to access the Internet. You can specify the private IP in the following ways:

     -   **Manually Input**: Enter the private IP that you want to map. It must be within the private IP range of the VPC.
    -   **Auto Fill**: Select an ECS instance in the VPC from the list. The private IP of the selected ECS instance is automatically entered in the field.
 |
    |**Port Settings**| DNAT supports IP mapping and port mapping. Select a mapping method:

     -   **All Ports**: Select this option to configure IP mapping.  Using this method, the ECS instance with the specified private IP can receive any Internet requests using any protocol on any port. This is the same as binding an EIP to the ECS instance.

    -   **Specific Port**: Select this option to configure port mapping. Using this method, NAT Gateway forwards the request from the specified protocol and port to the target ECs instance on the specified port.

You must specify the public port, private port, and IP protocol when the port mapping is selected.

 |


## Edit a DNAT entry {#section_mwp_tcl_32b .section}

To edit a DNAT entry, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.  Click the **Configure DNAT** option of the target NAT Gateway.
5.  Click **Edit** to edit the target DNAT entry.

## Delete a DNAT entry {#section_ofp_qdz_ydb .section}

To delete a DNAT entry, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the target NAT Gateway.
4.  Click the **Configure DNAT** option of the target NAT Gateway.
5.  Click **Remove**, and then click **OK** in the displayed dialog box.

