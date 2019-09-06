# Call APIs {#concept_354465 .concept}

NAT Gateway and VPC use the same service address \(endpoint\). This means that when you call NAT Gateway APIs, HTTP GET requests are sent to the API end point of NAT Gateway, and the system responds according to the parameters set in the request. Both the requests and responses are UTF-8 encoded.

## Request syntax {#section_zuw_3ka_5pp .section}

NAT Gateway APIs use RPC style. To call NAT Gateway APIs, send HTTP GET requests.

The structure of a NAT Gateway API request is as follows:

``` {#codeblock_8pu_orf_6tj}
http://Endpoint/?Action=xx&Parameters 
```

Where:

-   Endpoint: The endpoint of NAT Gateway APIs is `vpc.aliyuncs.com`.
-   Action: the name of the action. For example, if you need to create a NAT Gateway, the action is CreateNatGateway.
-   Version: The version of the API. The version of NAT Gateway APIs is 2016-04-28.
-   Parameters: the request parameters. Separate multiple parameters by using ampersands \(&\).

    Request parameters include common parameters and API-specific parameters. Common parameters include API version and identity authentication information among other parameters. For more information, see [Common parameters](../../../../intl.en-US/API reference/Common parameters.md#).


The following is an example of calling CreateNatGateway to create a NAT Gateway:

**Note:** The following code has been edited to improve readability.

``` {#codeblock_b1o_i0a_350}
https://vpc.aliyuncs.com/?Action=CreateNatGateway
&Format=xml
&Version=2016-04-28
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…
```

## API authorization {#section_2nv_byu_qu0 .section}

To maintain account security, we recommend that you use the Access Keys \(AKs\) of RAM users to call APIs. Before you call APIs using the AKs of RAM users, you need to grant permissions to the RAM users by attaching corresponding policies to them.

For more information about the policies related to NAT Gateway APIs, see [RAM authentication](../../../../intl.en-US/API reference/RAM authentication.md#).

## Request signature {#section_vo0_34q_uys .section}

Authentication is required by the NAT Gateway service for each API call, which is provided by the inclusion of signature information in the request.

NAT Gateway uses an AccessKeyID and AccessKeySecret pair \(that is, an AK\) and symmetric encryption to authenticate the identity of the request sender. AKs are certificates that Alibaba Cloud issues to Alibaba Cloud accounts and RAM users for authentication. It is similar to a logon password. The AccessKeyID is used to identify the visitor's identity. The AccessKeySecret is the key used to encrypt the signature string. The server uses the AccessKeySecret to decrypt the signature string. The AccessKeySecret must be kept confidential.

A request in an API call is signed in the following format:

`https://endpoint/?SignatureVersion=*1.0*&SignatureMethod=*HMAC-SHA1*&Signature=*XXXX%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx*`

Take the API call of CreateNatGateway as an example. If your AccessKey ID is `testid`, and your AccessKey Secret is `testsecret`, then, the URL in the signature is as follows:

``` {#codeblock_p94_qi3_5nc}
http://vpc.aliyuncs.com/?Action=CreateNatGateway
&Timestamp=2016-05-23T12:46:24Z
&Format=XML 
&AccessKeyId=testid 
&SignatureMethod=HMAC-SHA1 
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx
&Version=2014-05-26 
&SignatureVersion=1.0 
```

To generate the signature, follow these steps:

1.  Create the string to be signed by using the request parameter.

    ``` {#codeblock_ohr_vfo_4d4}
    GET&%2F&AccessKeyId%3Dtestid&Action%3DCreateNatGateway&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15 
    ```

    .

2.  Calculate the HMAC value of the string.

    Add an ampersand \(&\) after the AccessKeySecret to add the key of the HMAC value. In this example, the key is `testsecret&`.

    ``` {#codeblock_pep_jc2_8z4}
    CT9X0VtwR86fNWS********juE=
    ```

3.  Add the signature to the request parameter.

    ``` {#codeblock_cwj_fgd_l1l}
    http://vpc.aliyuncs.com/?Action=CreateNatGateway
    &Timestamp=2016-05-23T12:46:24Z 
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx 
    &Version=2014-05-26 
    &SignatureVersion=1.0 
    &Signature=XXXX%3D 
    ```


