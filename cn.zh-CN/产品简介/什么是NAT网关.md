# 什么是NAT网关 {#concept_wpm_kfy_ydb .concept}

NAT网关（NAT Gateway）是一款企业级的VPC公网网关，提供NAT代理（SNAT和DNAT）、高达10Gbps级别转发能力以及跨可用区的容灾能力。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13979/15616359714440_zh-CN.png)

NAT网关作为一个网关设备，需要绑定公网IP才能正常工作。创建NAT网关后，您可以为NAT网关绑定弹性公网IP（EIP）。

**说明：** 对于2017年11月3日之前账号下存在NAT带宽包的账号，您仍需使用NAT带宽包为该NAT网关提供公网IP。如需使用EIP绑定NAT网关功能，请提交工单。

如果您需要使用共享带宽功能，可以在EIP控制台将EIP加入已有的共享带宽，或者在购买共享带宽后，再将EIP加入到共享带宽中。详细说明，请参见[加入共享带宽](../../../../intl.zh-CN/用户指南/管理后付费EIP/加入共享带宽.md#)。

