# Multiple applications share the bandwidth {#concept_wbc_dfz_ydb .concept}

This topic describes how to enable multiple applications to share bandwidth through the DNAT and bandwidth sharing functions of a NAT Gateway to lower costs associated with Internet traffic.

## Scenario {#section_kwj_gfz_ydb .section}

Assume that four Internet-facing applications are deployed and three public IP addresses are required. Furthermore, a backup public IP address is also required. The network plan for the preceding scenario is as follows:

-   Bandwidth: 150Mbps
-   Number of public IP addresses: 5, of which one is the backup IP address.
-   Total number of ECS instances required: 5
-   Mappings between the public IP addresses and ECS instances:
    -   IP1-\>ECS1
    -   IP2-\>ECS2
    -   IP3-\>ECS3/ECS4 \(Port 80 is mapped to port 80 of ECS 3; port 443 is mapped to port 443 of ECS 4\)
    -   IP4-\>ECS5 \(O&M jump server\). Only port 22 is opened.
    -   IP5: The DNAT rule is not added for this IP address temporarily.

In addition, a VPC \(ID: vpc-11af8lxxx\) and multiple ECS instances are created. Note

that the private IP addresses of the ECS instances are as follows:

**Note:** You do not need to configure public IP addresses for the ECS instances.

|Instance name|Private IP address|
|:------------|:-----------------|
|ECS1|192.168.1.1|
|ECS2|192.168.1.2|
|ECS3|192.168.1.3|
|ECS4|192.168.1.4|

## Prerequisites {#section_mrk_121_hgb .section}

1.  For convenient API calling, this document provides a Python-based Command Line tool. Click [Here](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/32327/cn_zh/1469718485900/api.py?spm=a2c4g.11186623.2.4.kwCDtJ&file=api.py) to download the CLI tool.

    The tool can be directly downloaded by running the wget command in Linux.

    ``` {#codeblock_q00_zyh_5vx}
    wget http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/42691/cn_zh/1468947102311/api.py
    ```

2.  Create an AccessKey.

    You need to create an AccessKey for the account that calls the API action.

3.  Configure the AccessKey for the CLI tool.

## Step 1: Create a NAT Gateway {#section_omu_q61_yk3 .section}

1.  Call CreateNatGateway to create a NAT Gateway.

    ``` {#codeblock_n6x_4uc_zfu}
    [admin@tester:xxx]$ python api.py CreateNatGateway RegionId=cn-shanghai VpcId=vpc-11af8lxxx BandwidthPackage. 1.IpCount=4 BandwidthPackage. 1.Bandwidth=150 BandwidthPackage. 1.Zone=cn-shanghai-a Name=MyNatGW Description="My first NAT Gateway"
     =====Request URL======
     https://ecs.aliyuncs.com/?SignatureVersion=1.0&VpcId=vpc-11af8lxxx&Name=MyNatGW&Format=json&TimeStamp=2016-05-23T03%3A26%3A21Z&BandwidthPackage. 1.IpCount=5&RegionId=cn-shanghai&AccessKeyId=jZgi0oyrQXXXXXXX&SignatureMethod=HMAC-SHA1&Version=2014-05-26&Signature=I4KKhWgjJdImTqk4rCifAB3LbLw%3D&action=CreateNatGateway&SignatureNonce=1ebae49c-2096-11e6-b781-2cf0ee28adf2&BandwidthPackage. 1.Bandwidth=150&BandwidthPackage. 1.Zone=cn-shanghai-a&Description=My+first+NAT+Gateway
     =====Request URL end======
     ====== Got Response ======
     {
       "BandwidthPackageIds": {
         "BandwidthPackageId": [
           "bwp-11odxu2k7"
         ]
       },
       "ForwardTableIds": {
         "ForwardTableId": [
           "ftb-11tc6xgmv"
         ]
       },
       "NatGatewayId": "ngw-112za33e4",
       "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
    ```

2.  Call DescribeNatGateways to view the detailed information of a NAT Gateway.

    ``` {#codeblock_g25_mm9_5fr}
    [admin@tester:xxx]$ python api.py DescribeNatGateways RegionId=cn-shanghai VpcId=vpc-11af8lxxx
     =====Request URL======
     https://ecs.aliyuncs.com/?SignatureVersion=1.0&VpcId=vpc-11af8lxxx&Format=json&TimeStamp=2016-05-23T03%3A27%3A14Z&RegionId=cn-shanghai&AccessKeyId=jZgi0oyrQ6ihgKp9&SignatureMethod=HMAC-SHA1&Version=2014-05-26&Signature=JvXErso9g0fZdRTgBtNLepe%2F1e4%3D&action=DescribeNatGateways&SignatureNonce=3e1424eb-2096-11e6-bc31-2cf0ee28adf2
     =====Request URL end======
     ====== Got Response ======
     {
       "NatGateways": {
         "NatGateway": [
           {
             "BandwidthPackageIds": {
               "BandwidthPackageId": [
                 "bwp-11odxu2k7"
               ]
             },
             "BusinessStatus": "Normal",
             "CreationTime": "2016-05-23T03:26:23Z",
             "Description": "My first NAT Gateway",
             "ForwardTableIds": {
               "ForwardTableId": [
                 "ftb-11tc6xgmv"
               ]
             },
             "InstanceChargeType": "PostPaid",
             "Name": "MyNatGW",
             "NatGatewayId": "ngw-112za33e4",
             "RegionId": "cn-shanghai",
             "Spec": "Small",
             "Status": "Available",
             "VpcId": "vpc-11af8lxxx"
           }
         ]
       },
       "PageNumber": 1,
       "PageSize": 10,
       "RequestId": "FE4C442C-9778-449A-BF7F-7F36C3AF5611",
       "TotalCount": 1
     }
    ```

3.  Call DescribeBandwidthPackages to view the detailed information of the created shared bandwidth packages.

    ``` {#codeblock_x10_08d_otn}
    [admin@tester:xxx]$ python api.py DescribeBandwidthPackages RegionId=cn-shanghai NatGatewayId=ngw-112za33e4
     =====Request URL======
     https://ecs.aliyuncs.com/?SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A33%3A30Z&RegionId=cn-shanghai&NatGatewayId=ngw-112za33e4&AccessKeyId=jZgi0oyrQ6ihgKp9&SignatureMethod=HMAC-SHA1&Version=2014-05-26&Signature=KN0C2Q4TUZtfECBn1c2lOdBzrb8%3D&action=DescribeBandwidthPackages&SignatureNonce=1e8941ae-2097-11e6-acbb-2cf0ee28adf2
     =====Request URL end======
     ====== Got Response ======
     {
       "BandwidthPackages": {
         "BandwidthPackage": [
           {
             "Bandwidth": "150",
             "BandwidthPackageId": "bwp-11odxu2k7",
             "BusinessStatus": "Normal",
             "CreationTime": "2016-05-23T03:26:24Z",
             "Description": "",
             "InstanceChargeType": "PostPaid",
             "InternetChargeType": "PayByBandwidth",
             "IpCount": "5",
             "Name": "",
             "NatGatewayId": "ngw-112za33e4",
             "PublicIpAddresses": {
               "PublicIpAddresse": [
                 {
                   "AllocationId": "nateip-11iopy3sl",
                   "IpAddress": "139.xxx.xx. 107"
                 },
                 {
                   "AllocationId": "nateip-11pt1f9ph",
                   "IpAddress": "139.xxx.xx. 55"
                 },
                 {
                   "AllocationId": "nateip-111ul670c",
                   "IpAddress": "139.xxx.xx. 79"
                 },
                 {
                   "AllocationId": "nateip-11ogfjj85",
                   "IpAddress": "139.xxx.xx. 59"
                 },
                 {
                   "AllocationId": "nateip-11s2jempe",
                   "IpAddress": "139.xxx.xx. 58"
                 }
               ]
             },
             "RegionId": "cn-shanghai",
             "Status": "Available",
             "ZoneId": "cn-shanghai-a"
           }
         ]
       },
       "PageNumber": 1,
       "PageSize": 10,
       "RequestId": "14406B86-7CA1-4907-9755-86096F476A4F",
       "TotalCount": 1
     }
    ```


## Step 2: Configure DNAT entries {#section_z9d_xqo_qbd .section}

1.  Call CreateForwardEntry to add the following forwarding entries.

    |Public IP address|Public port|Private IP address|Private port|Protocol|
    |:----------------|:----------|:-----------------|:-----------|:-------|
    |IP1|Any|ecs-ip1|Any|Any|
    |IP2|Any|ecs-ip2|Any|Any|
    |IP3|80|ecs-ip3|80|TCP|
    |IP3|443|ecs-ip4|443|TCP|
    |IP4|22|ecs-ip5|22|TCP|

    ``` {#codeblock_z1j_due_go5}
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 107 ExternalPort=Any InternalIp=192.168.1.1 InternalPort=Any IpProtocol=Any
    =====Request URL======
    https://ecs.aliyuncs.com/?ExternalIp=139.xxx.xx. 107&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A53%3A18Z&RegionId=cn-shanghai&ExternalPort=Any&InternalIp=192.168.1.1&Signature=iR4GSzhJQtowMJOj%2FRth3ABP4FA%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=Any&action=CreateForwardEntry&SignatureNonce=e2ceae11-2099-11e6-b548-2cf0ee28adf2&InternalPort=Any 
    =====Request URL end======
    ====== Got Response ======
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 107 ExternalPort=Any InternalIp=192.168.1.1 InternalPort=Any IpProtocol=Any
    =====Request URL======
    https://ecs.aliyuncs.com/?ExternalIp=139.xxx.xx. 107&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A53%3A18Z&RegionId=cn-shanghai&ExternalPort=Any&InternalIp=192.168.1.1&Signature=iR4GSzhJQtowMJOj%2FRth3ABP4FA%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=Any&action=CreateForwardEntry&SignatureNonce=e2ceae11-2099-11e6-b548-2cf0ee28adf2&InternalPort=Any 
    =====Request URL end======
    ====== Got Response ======
    {
    "ForwardEntryId": "fwd-119smw5tk",
    "RequestId": "A4AEE536-A97A-40EB-9EBE-53A6948A6928"
    }
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 55 ExternalPort=Any InternalIp=192.168.1.2 InternalPort=Any IpProtocol=Any
    =====Request URL======
    https://ecs.aliyuncs.com/?ExternalIp=139.xxx.xx. 55&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A53%3A42Z&RegionId=cn-shanghai&ExternalPort=Any&InternalIp=192.168.1.2&Signature=mFBn%2BCd4LfHkKj53MwmWyMhzyfs%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=Any&action=CreateForwardEntry&SignatureNonce=f09c1b38-2099-11e6-aa80-2cf0ee28adf2&InternalPort=Any 
    =====Request URL end======
    ====== Got Response ======
    {
    "ForwardEntryId": "fwd-11dz3ly9l",
    "RequestId": "5DBC8F86-2D76-4BF4-B839-7FF31B61D516"
    }
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 79 ExternalPort=80 InternalIp=192.168.1.3 InternalPort=80 IpProtocol=TCP
    =====Request URL======
    https://ecs.aliyuncs.com/?ExternalIp=139.xxx.xx. 79&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A54%3A10Z&RegionId=cn-shanghai&ExternalPort=80&InternalIp=192.168.1.3&Signature=OpTui3SKbAjKXy6gKRoJb%2B9Lazg%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=TCP&action=CreateForwardEntry&SignatureNonce=01c41d5c-209a-11e6-905e-2cf0ee28adf2&InternalPort=80 
    =====Request URL end======
    ====== Got Response ======
    {
    "ForwardEntryId": "fwd-11r23r7p5",
    "RequestId": "67B7AAFD-E7AB-4EB8-AA5C-AA38CFFB4A95"
    }
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 79 ExternalPort=443 InternalIp=192.168.1.4 InternalPort=443 IpProtocol=TCP
    =====Request URL======
    Https://ecs.aliyuncs.com /? ExternalIp = 139. xxx. xx. 79&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A55%3A22Z&RegionId=cn-shanghai&ExternalPort=443&InternalIp=192.168.1.4&Signature=X%2BZtHbTeKYf8xU%2FvWhPAmg%2B5scc%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=TCP&action=CreateForwardEntry&SignatureNonce=2c3f2573-209a-11e6-be0f-2cf0ee28adf2&InternalPort=443 
    =====Request URL end======
    ====== Got Response ======
    {
    "ForwardEntryId": "fwd-11cdhpjlk",
    "RequestId": "260A9673-5522-4F66-844A-1F1AB47CD21C"
    }
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$
    [admin@tester:xxx]$ python api.py CreateForwardEntry RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv ExternalIp=139.xxx.xx. 59 ExternalPort=22 InternalIp=192.168.1.5 InternalPort=22 IpProtocol=TCP
    =====Request URL======
    https://ecs.aliyuncs.com/?ExternalIp=139.xxx.xx. 59&SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A55%3A44Z&RegionId=cn-shanghai&ExternalPort=22&InternalIp=192.168.1.5&Signature=%2FZWf5%2ForHr%2BUR446eEBLC4LNYe8%3D&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&IpProtocol=TCP&action=CreateForwardEntry&SignatureNonce=39863cf3-209a-11e6-8f6d-2cf0ee28adf2&InternalPort=22 
    =====Request URL end======
    ====== Got Response ======
    {
    "ForwardEntryId": "fwd-11iv34uj7",
    "RequestId": "0884BC12-8EAD-4AAA-826E-30E5435D7C27"
    }
    ```

2.  Call DescribeForwardTableEntries to view the added DNAT entries.

    ``` {#codeblock_1x5_t1i_8ar}
    [admin@tester:xxx]$ python api.py DescribeForwardTableEntries RegionId=cn-shanghai ForwardTableId=ftb-11tc6xgmv
     =====Request URL======
     https://ecs.aliyuncs.com/?SignatureVersion=1.0&Format=json&TimeStamp=2016-05-23T03%3A56%3A18Z&RegionId=cn-shanghai&AccessKeyId=jZgi0oyrQ6ihgKp9&ForwardTableId=ftb-11tc6xgmv&SignatureMethod=HMAC-SHA1&Version=2014-05-26&Signature=x4%2B6oNYxIRBmND8rcIbJM9EJ8ts%3D&action=DescribeForwardTableEntries&SignatureNonce=4db93223-209a-11e6-81eb-2cf0ee28adf2
     =====Request URL end======
     ====== Got Response ======
     {
       "ForwardTableEntries": {
         "ForwardTableEntry": [
           {
             "ExternalIp": "139.xxx.xx. 107",
             "ExternalPort": "any",
             "ForwardEntryId": "fwd-119smw5tk",
             "ForwardTableId": "ftb-11tc6xgmv",
             "InternalIp": "192.168.1.1",
             "InternalPort": "any",
             "IpProtocol": "any",
             "Status": "Available"
           },
           {
             "ExternalIp": "139.xxx.xx. 79",
             "ExternalPort": "443",
             "ForwardEntryId": "fwd-11cdhpjlk",
             "ForwardTableId": "ftb-11tc6xgmv",
             "InternalIp": "192.168.1.4",
             "InternalPort": "443",
             "IpProtocol": "tcp",
             "Status": "Available"
           },
           {
             "ExternalIp": "139.xxx.xx. 55",
             "ExternalPort": "any",
             "ForwardEntryId": "fwd-11dz3ly9l",
             "ForwardTableId": "ftb-11tc6xgmv",
             "InternalIp": "192.168.1.2",
             "InternalPort": "any",
             "IpProtocol": "any",
             "Status": "Available"
           },
           {
             "ExternalIp": "139.xxx.xx. 59",
             "ExternalPort": "22",
             "ForwardEntryId": "fwd-11iv34uj7",
             "ForwardTableId": "ftb-11tc6xgmv",
             "InternalIp": "192.168.1.5",
             "InternalPort": "22",
             "IpProtocol": "tcp",
             "Status": "Available"
           },
           {
             "ExternalIp": "139.xxx.xx. 79 ",
             "ExternalPort": "80",
             "ForwardEntryId": "fwd-11r23r7p5",
             "ForwardTableId": "ftb-11tc6xgmv",
             "InternalIp": "192.168.1.3",
             "InternalPort": "80",
             "IpProtocol": "tcp",
             "Status": "Available"
           }
         ]
       },
       "PageNumber": 1,
       "PageSize": 10,
       "RequestId": "C84FDDCF-8550-4024-B89C-01E7459D7CF9",
       "TotalCount": 5
     }
    ```


