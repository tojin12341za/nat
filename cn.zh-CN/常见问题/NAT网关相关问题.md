# NAT网关相关问题 {#concept_270217 .concept}

-   [一个公网IP可以同时设置DNAT和SNAT规则吗？](#section_vlv_m2f_2bf)
-   [一个阿里云账号可以创建多少个NAT网关？](#section_0wp_8zk_c6u)
-   [一个NAT网关可以创建多少条DNAT条目？](#section_igf_d4c_mui)
-   [一个NAT网关可以创建多少条SNAT条目？](#section_rsx_1cu_8cd)
-   [一个SNAT条目支持关联多少个公网IP？](#section_oyo_bvw_tt3)
-   [NAT网关支持从后付费类型转换为预付费吗？](#section_qtr_l14_s8u)
-   [NAT网关支持从预付费类型转换为后付费吗？](#section_bfh_56b_d4r)
-   [NAT网关支持查看每个交换机的流量吗？](#section_vcs_0wp_vsg)

## 一个公网IP可以同时设置DNAT和SNAT规则吗？ {#section_vlv_m2f_2bf .section}

不支持。需要分别绑定不同的公网IP来设置DNAT规则和SNAT规则。

## 一个阿里云账号可以创建多少个NAT网关？ {#section_0wp_8zk_c6u .section}

每个VPC仅能创建1个NAT网关。不针对阿里云账号限制NAT网关的数量。

## 一个NAT网关可以创建多少条DNAT条目？ {#section_igf_d4c_mui .section}

一个NAT网关最多可添加100条DNAT条目。

您可以在配额管理页面，找到配额名称natgw\_quota\_dnat\_entry\_num，然后申请调整。

## 一个NAT网关可以创建多少条SNAT条目？ {#section_rsx_1cu_8cd .section}

一个NAT网关最多可添加40条SNAT条目。

您可以在配额管理页面，找到配额名称natgw\_quota\_snat\_entry\_num，然后申请调整。

## 一个SNAT条目支持关联多少个公网IP？ {#section_oyo_bvw_tt3 .section}

默认256个，不支持调整。

## NAT网关支持从后付费类型转换为预付费吗？ {#section_qtr_l14_s8u .section}

支持。

## NAT网关支持从预付费类型转换为后付费吗？ {#section_bfh_56b_d4r .section}

不支持。

## NAT网关支持查看每个交换机的流量吗？ {#section_vcs_0wp_vsg .section}

不支持。

您可以为每个交换机绑定一个EIP，然后通过查看EIP获取交换机的流量。

