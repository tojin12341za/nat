# Create an SNAT entry {#task_wsl_11z_ydb .task}

The SNAT function provides the Internet proxy service for the ECS instances of the VPC network. Therefore, the ECS instances can access the Internet.

You have created a NAT Gateway and an EIP.

**Note:** If your account has purchased a bandwidth package before January 26, 2018, the public IP is the IP of the bandwidth package.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **NAT Gateways**. 
3.   Select the region of the NAT Gateway. 
4.   Click the instance ID of the target NAT Gateway. 
5.   In the left-side navigation pane, click **SNAT Table**, and then click **Create SNAT Entry**. 
6.   Configure the SNAT entry according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |**VSwitch**| Select the VSwitch where the ECS instances that require the Internet access are located. All ECS instances in the specified VSwitch can use the specified public IP to access the Internet.

 **Note:** If an ECS instance has already configured a public IP \(such as an EIP\), the pre-configured public IP is used to access the Internet instead of using the SNAT proxy service.

 |
    |**VSwitch CIDR block**|Display the CIDR block of the selected VSwitch.|
    |**Internet IP Address**| Select public IP that is used to access the Internet.

 **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |

    |Configuration|Description|
    |:------------|:----------|
    |**VSwitch**| Select the VSwitch where the ECS instances that require the Internet access are located. All ECS instances in the specified VSwitch can use the specified public IP to access the Internet.

 **Note:** If an ECS instance has already configured a public IP \(such as an EIP\), the pre-configured public IP is used to access the Internet instead of using the SNAT proxy service.

 |
    |**VSwitch CIDR block**|Display the CIDR block of the selected VSwitch.|
    |**Internet IP Address**| Select public IP that is used to access the Internet.

 **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |


