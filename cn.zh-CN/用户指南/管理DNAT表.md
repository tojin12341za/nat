# 管理DNAT表 {#concept_czl_mcz_ydb .concept}

NAT网关提供DNAT功能，将NAT网关上的公网IP映射给专有网络的ECS实例使用，使ECS可以面向互联网提供服务。

## DNAT条目 {#section_gsb_pcz_ydb .section}

NAT网关将DNAT功能的配置，抽象为一张DNAT列表。您可以通过配置DNAT列表中的DNAT条目，实现DNAT功能的配置。

每个DNAT条目由五部分组成：公网IP、公网端口、私网IP、私网端口和协议。其中公网IP为NAT网关绑定的弹性公网IP（EIP），私网IP为专有网络中ECS实例的IP。配置DNAT条目后，公网IP收到的数据将按照自定义的映射规则，转发给专有网络VPC内的ECS。

**说明：** 对于2018年1月26日之前账户下存在NAT带宽包的用户，DNAT条目中的公网IP为NAT带宽包提供的公网IP。

## 端口映射和IP映射 {#section_mkg_wcz_ydb .section}

DNAT功能包括端口映射与IP映射：

-   端口映射

    配置端口后，NAT网关会将以指定协议和端口访问该公网IP的请求转发到目标ECS实例的指定端口上。例如下表中的条目1和条目2。

-   IP映射

    配置IP映射后，相当于为目标ECS实例配置了一个弹性公网IP。任何访问该公网IP的请求都将转发到目标ECS实例上。例如下表中的条目3。

    |转发条目|公网IP|公网端口|私网IP|私网端口|协议|
    |:---|:---|:---|:---|:---|:-|
    |条目1|139.224.xx.xx|80|192.168.x.x|80|TCP|
    |条目2|139.224.xx.xx|8080|192.168.x.x|8000|UDP|
    |条目3|139.224.xx.xx|Any|192.168.x.x|Any|Any|


## 添加DNAT条目 {#section_dv2_bdz_ydb .section}

完成以下操作，添加DNAT条目：

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  单击目标NAT网关的实例ID。
5.  在左侧导航栏，单击**DNAT列表**，然后单击**创建DNAT条目**。
6.  根据以下信息，配置DNAT条目。

    |配置|说明|
    |:-|:-|
    |**公网IP地址**| 选择一个可用的公网IP。

 **说明：** 用于创建SNAT条目的公网IP地址不能再用来创建DNAT条目。

 |
    |**私网IP地址**| 选择要通过DNAT规则进行公网通信的ECS实例。您可以通过以下两种方式指定目标ECS实例的私网IP：

     -   **自填**：输入目标ECS实例的私网IP。
    -   **从ECS对应IP进行选择**：从ECS实例列表中选择ECS实例，系统自动填充IP地址。
 |
    |**端口设置**| 选择DNAT映射的方式：

     -   **所有端口**：该方式属于IP映射，相当于为目标ECS实例配置了一个弹性公网IP。任何访问该公网IP的请求都将转发到目标ECS实例上。

    -   **具体端口**：该方式属于端口映射，NAT网关会将以指定协议和端口访问该公网IP的请求转发到目标ECS实例的指定端口上。

选择具体端口后，请根据业务需求输入公网端口（源端口）、私网端口（目的端口）和协议类型。

 |


## 编辑DNAT条目 {#section_mwp_tcl_32b .section}

完成以下操作，编辑DNAT条目：

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  单击目标NAT网关的**设置DNAT**选项。
5.  单击目标DNAT条目的**编辑**，更新DNAT条目配置。

## 删除DNAT条目 {#section_ofp_qdz_ydb .section}

完成以下操作，删除：

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  单击目标NAT网关的**设置DNAT**选项。
5.  单击目标DNAT条目的**移除**，然后单击**确定**。

