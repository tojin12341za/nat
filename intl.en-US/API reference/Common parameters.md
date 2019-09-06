# Common parameters {#reference_xry_cjk_qdb .reference}

## Common request parameters {#section_zm5_rgf_cz .section}

The following table describes common request parameters used in most Alibaba Cloud APIs.

|Parameter|Type|Required?|Description|
|:--------|:---|:--------|:----------|
|Format|String|No|The format of the response. Valid values: JSON \(default\) | XML

 |
|Version|String|Yes|The version of the API. It uses the date format `YYYY-MM-DD`. Valid value: 2016-04-28

 |
|AccessKeyId|String|Yes|The AccessKey ID of the user who calls the API.|
|Signature|String|Yes|The request signature.|
|SignatureMethod|String|Yes|The algorithm used to create the request signature. Valid value: HMAC-SHA1

 |
|Timestamp|String|Yes|The time at which the request is signed. It uses the format: `YYYY-MM-DDThh:mm:ssZ`. For example, 2013-01-10T12:00:00Z.

 |
|SignatureVersion|String|Yes|The signature version to use. Valid value: 1.0

 |
|SignatureNonce|String|Yes|A random number for the signature to prevent from network attacks. Different random numbers must be used for different requests.

 |

## Common response parameters {#section_rjn_1hf_cz .section}

Alibaba Cloud API responses all use a unified format. A status code of the format 2xx indicates a successful call, and a status code of the 4xx or 5xx format indicates a failed call. For successful calls, returned data can be in a XML or JSON format. You can specify the format of the returned data when sending a request. The default format is XML.

A RequestId is returned no matter if it is successful or not.

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? > 
        <!—The root node of the result-->
        <Action+Response>
            <!—The returned result-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!—The returned result-->
        </Action+Response>
    					
    ```

-   JSON format

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*The returned result*/
        }
    ```


