# View monitoring data {#task_eb2_ft2_2hb .task}

Because NAT Gateway interoperates with Alibaba CloudMonitor, you can view the monitoring data of NAT Gateway, such as the number of connections, and the number of discarded connections due to the capacity or speed limit being reached.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **NAT Gateways**. 
3.   Select the region of the NAT Gateway. 
4.   On the NAT Gateways page, find the target NAT Gateway and click the ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/147949/156160012941324_en-US.png) icon in the **SNAT Connections** column. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/147949/156160012941328_en-US.png)

    Monitoring metrics of a NAT Gateway are shown in the following table:

    |Item|Description|Dimension|Unit |Minimum monitoring granularity|
    |----|-----------|---------|-----|------------------------------|
    |SNAT connections|The number of SNAT connections of a NAT Gateway instance.|Instance|Count/Min|30s|
    |Capacity Limit discarded connections|The maximum number of SNAT connections vary according to the NAT Gateway specification. Capacity limit discarded connections indicate the SNAT connections that are dropped when the number of connections to the instance exceeds the maximum number of SNAT connections corresponding to the specification of the instance. **Note:** This metric is an accumulated value and will not be reset.

     -   If the number of capacity limit discarded connections increase continuously during a certain period of time, we recommend that you upgrade the specification of NAT Gateway.
    -   If a horizontal line is displayed during a certain period of time, it indicates that no packets were dropped during this time period.
 |Instance|Count/Min|30s|
    |Speed limit discarded connections|The maximum number of SNAT connections per second vary according to the NAT Gateway specification. Speed limit discarded connections indicate the number of SNAT connections that are dropped when the number of SNAT connections to the instance per second exceeds the maximum number of SNAT connections per second corresponding to the specification of the instance. **Note:** This metric is an accumulated value and will not be reset.

     -   If the number of speed limit discarded connections increase continuously during a certain period of time, we recommend that you upgrade the specification of the NAT Gateway.
    -   If a horizontal line is displayed during a certain period of time, it indicates that no packets were dropped during this time period.
 |Instance|Count/Min|30s|


