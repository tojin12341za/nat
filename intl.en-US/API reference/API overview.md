# API overview {#concept_354462 .concept}

The following table lists available NAT Gateway API actions. The endpoint of NAT Gateway API actions is vpc.aliyuncs.com. For more information on how to call NAT Gateway API actions, see the VPC API documentation.

|API|Description|
|---|-----------|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2533.md\#](../../../../intl.en-US/API reference/NAT Gateway/CreateNatGateway.md#)|Creates a NAT Gateway.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2536.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifyNatGatewayAttribute.md#)|Modifies the name and description of a NAT Gateway.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2535.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifyNatGatewaySpec.md#)|Modifies the specifications of a NAT Gateway.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2534.md\#](../../../../intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md#)|Queries created NAT Gateways.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2547.md\#](../../../../intl.en-US/API reference/NAT Gateway/CreateForwardEntry.md#)|Adds a DNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2549.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifyForwardEntry.md#)|Modifies a DNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2548.md\#](../../../../intl.en-US/API reference/NAT Gateway/DescribeForwardTableEntries.md#)|Queries DNAT entries in a DNAT table.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2550.md\#](../../../../intl.en-US/API reference/NAT Gateway/DeleteForwardEntry.md#)|Deletes a DNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2551.md\#](../../../../intl.en-US/API reference/NAT Gateway/CreateSnatEntry.md#)|Creates an SNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2553.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifySnatEntry.md#)|Modifies an SNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2552.md\#](../../../../intl.en-US/API reference/NAT Gateway/DescribeSnatTableEntries.md#)|Queries SNAT entries in a SNAT table.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2554.md\#](../../../../intl.en-US/API reference/NAT Gateway/DeleteSnatEntry.md#)|Deletes an SNAT entry.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2540.md\#](../../../../intl.en-US/API reference/NAT Gateway/CreateBandwidthPackage.md#)|Creates a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2541.md\#](../../../../intl.en-US/API reference/NAT Gateway/DescribeBandwidthPackages.md#)|Queries NAT bandwidth packages.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2542.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifyBandwidthPackageSpec.md#)|Modifies the bandwidth of a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2543.md\#](../../../../intl.en-US/API reference/NAT Gateway/ModifyBandwidthPackageAttribute.md#)|Modifies the name and description of a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2544.md\#](../../../../intl.en-US/API reference/NAT Gateway/AddBandwidthPackageIps.md#)|Adds a public IP address to a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2545.md\#](../../../../intl.en-US/API reference/NAT Gateway/RemoveBandwidthPackageIps.md#)|Removes a public IP address from a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2546.md\#](../../../../intl.en-US/API reference/NAT Gateway/DeleteBandwidthPackage.md#)|Deletes a NAT bandwidth package.|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/EN-US\_TP\_2537.md\#](../../../../intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md#)|Deletes a NAT Gateway.|

**Note:** You can call DescribeBandwidthPackages, ModifyBandwidthPackageSpec, AddBandwidthPackageIps, RemoveBandwidthPackageIps, and DeleteBandwidthPackage only if you purchased a NAT bandwidth package before January 26, 2018. If you did not purchase a NAT bandwidth package before January 26, 2018, use an EIP.

