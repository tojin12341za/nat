# NAT网关优化公告 {#concept_1340467 .concept}

为提升NAT网关产品使用体验，NAT网关从对于2017年11月4日由NAT带宽包切换为EIP绑定NAT网关实例的使用方式。

## NAT网关使用优化升级 {#section_bww_dhr_33c .section}

使用流程变更如下：

-   2017年11月3日 23：59分之前购买过NAT网关带宽包的使用流程：

    1. 购买NAT网关—\>2. 购买NAT带宽包—\>3. 设置SNAT/DNAT规则

-   2017年11月3日 23：59分之后新购买NAT网关且不存在NAT网关带宽包的使用流程：

    1. 购买NAT网关—\>2. 在NAT网关上绑定EIP —\>3. 设置SNAT/DNAT规则

    **说明：** 在使用新流程中如果希望额外实现带宽共享功能，请在[EIP控制台](https://ip.console.aliyun.com/)[共享带宽](https://www.aliyun.com/product/cbwp)


## 升级覆盖的用户 {#section_oyn_jj9_wwy .section}

-   对于2017年11月3日 23：59分之前账号下没有NAT带宽包的全部用户，使用流程升级为EIP绑定NAT的形式。EIP绑定NAT网关的方式，请参见[绑定和解绑EIP](https://help.aliyun.com/document_detail/61834.html)
-   
