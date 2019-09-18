# Migrate a a self-built SNAT gateway to NAT Gateway {#task_ipr_2rb_zdb .task}

This tutorial illustrates how to migrate a self-built SNAT gateway to NAT Gateway.

If you want to switch over from a self-built SNAT gateway on an ECS instance to the SNAT function based on NAT Gateway, you can remove the self-built SNAT gateway and then create and configure a NAT gateway. However, this will interrupt the SNAT function for a period of time.

The recommended best practice is to follow these steps to seamlessly switch over to a NAT gateway of Alibaba Cloud by using the longest match principle of the route table. During the switching process, the SNAT function will always be available. Interruption of the existing TCP connection only occurs at the instant of switching and you only need to reconnect the application.

The VPC and ECS configurations used in this tutorial are as follows:

-   Two ECS instances are created in the VPC:

    -   ECS \(i-9410jxxxx\) that is configured with a self-built SNAT gateway and is associated with an EIP. It also enables forwarding service and configures Iptables rules to achieve SNAT forwarding.
    -   ECS \(i-94kjwxxxx\) that requires the SNAT function to access the Internet.
-   A custom route entry of which the destination CIDR block is 0.0.0.0/0 and the next hop is ECS \(i-9410jxxxx\) is added to the VRouter of the VPC.


1.  Add the following eight route entries in the VPC to overwrite existing route entries. 

    The destination CIDR blocks are 1.0.0.0/8, 2.0.0.0/7, 4.0.0.0/6, 8.0.0.0/5, 16.0.0.0/4, 32.0.0.0/3, 64.0.0.0/2, 128.0.0.0/1, respectively, and the next hop is always ECS i-9410jxxxx.

    According to the longest match principle, a route entry with the longest subnet mask will always be matched first. However, all data packets, regardless of their IP addresses, will be matched to one of the eight entries. Therefore, the route entry, of which the destination CIDR block is 0.0.0.0/0, is not applied any more.

2.  Delete the route entry of which the destination CIDR block is 0.0.0.0/0.
3.  Create a NAT gateway. 

    A route entry, of which the destination CIDR block is 0.0.0.0/0, pointing to the NAT gateway, is automatically added when you create the NAT Gateway.

4.  Associate EIPs with the NAT Gateway. 

    **Note:** Ensure the bandwidth of the EIPs associated with the NAT Gateway is the same as the bandwidth of the self-built NAT gateway. If you have added an SNAT entry to the NAT Gateway, the outbound traffic from the ECS instance specified in the SNAT entry will be limited by the bandwidth of the NAT Gateway.

5.  Add SNAT entries.
6.  Delete the eight route entries added in Step 1, so that the VRouter will forward requests from the Internet to the NAT Gateway instead of the self-built SNAT. 

    Till now, the migration from the self-built SNAT gateway to the SNAT function of the NAT gateway on Alibaba Cloud is completed.


