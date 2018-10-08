# Add a DNAT entry {#task_csx_xyy_ydb .task}

You can use the DNAT function to map a public IP to a private IP of an ECS instance in the VPC network. Then, the ECS instance with the specified public IP can provide public services.

You have created a NAT Gateway and an EIP.

**Note:** If your account has purchased a bandwidth package before January 26, 2018, the public IP is the IP of the bandwidth package.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **NAT Gateways**. 
3.   Select the region of the NAT Gateway. 
4.   Click the ID of the target NAT Gateway. 
5.   In the left-side navigation pane, click **DNAT Table**, and then click **Create DNAT Entry**. 
6.   Configure the DNAT entry according to the following information. 

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


