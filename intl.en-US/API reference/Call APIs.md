# Call APIs {#concept_jyw_13k_qdb .concept}

Express Connect and VPC use the same service address \(endpoint\). This means that when you call Express Connect APIs, HTTP GET requests are sent to the API service address of Express Connect, and the system responds according to the parameters set in the request. Both the requests and responses are UTF-8 encoded.

## Request syntax {#section_mqj_q3f_mdb .section}

Express Connect APIs use RPC style. To call Express Connect APIs, send HTTP GET requests.

The structure of an Express Connect API request is as follows:

``` {#codeblock_g6s_y8b_t7d}
http://Endpoint/?Action=xx&Parameters
```

where,

-   Endpoint: The service address of Express Connect APIs is `vpc.aliyuncs.com`.
-   Action: the name of the action. For example, if you need to query created Express Connect instances, the action is DescribePhysicalConnections.
-   Version: the version of the API. The version of Express Connect APIs is 2016-04-28.
-   Parameters: the request parameters. Separate multiple parameters by using ampersands \(&\).

    Request parameters include common parameters and API-specific parameters. Common parameters include API version and identity authentication information among other parameters. For more information, see [Common parameters](../../../../reseller.en-US/API reference/Common parameters.md#).


The following is an example of calling DescribePhysicalConnections to query created physical connections.

**Note:** Note that the following code has been edited to ease readability.

``` {#codeblock_0cy_n0o_m3g}
https://vpc.aliyuncs.com/?Action=DescribePhysicalConnections
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

## User authentication {#section_mlp_qmf_mdb .section}

To maintain account security, we recommend that you use the Access Keys \(AKs\) of RAM users to call APIs. Before you call APIs by using the AKs of RAM users, you need to grant permissions to the RAM users by attaching corresponding policies to them.

For more information about the policies related to Express Connect APIs, see [RAM authentication](../../../../reseller.en-US/API reference/RAM authentication.md#).

## Request signature {#section_jtc_ymf_mdb .section}

Authentication is required by the Express Connect service for each API call, which is provided by the inclusion of signature information in the request.

Express Connect uses an AccessKeyID and AccessKeySecret pair \(that is, an AK\) and symmetric encryption to authenticate the identity of the request sender. AKs are certificates that Alibaba Cloud issues to Alibaba Cloud accounts and RAM users for authentication. It is similar to a logon password. The AccessKeyID is used to identify the visitor's identity. The AccessKeySecret is the key used to encrypt the signature string. The server uses the AccessKeySecret to decrypt the signature string. The AccessKeySecret must be kept confidential.

A request in an API call is signed in the following format:

`https://endpoint/?SignatureVersion=*1.0*&SignatureMethod=*HMAC-SHA1*&Signature=*XXXX%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf*`

Take the API call of DescribePhysicalConnections as an example. If your AccessKeyID is `testid`, and your AccessKeySecret is `testsecret`, then, the URL in the signature is as follows:

``` {#codeblock_f3a_43r_uzh}
http://vpc.aliyuncs.com/?Action=DescribePhysicalConnections
&Timestamp=2016-05-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2014-05-26
&SignatureVersion=1.0
```

To generate the signature, follow these steps:

1.  Create the string to be signed by using the request parameter.

    ``` {#codeblock_439_jnb_rmh}
    GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribePhysicalConnections&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15
    ```

    .

2.  Calculate the HMAC value of the string.

    Add an ampersand \(&\) after the AccessKeySecret to add the key of the HMAC value. In this example, the key is `testsecret&`.

    ``` {#codeblock_q24_6hl_t1s}
    CT9X0VtwR86fNWS********juE=
    ```

3.  Add the signature to the request parameter.

    ``` {#codeblock_yju_9ve_q5d}
    http://vpc.aliyuncs.com/?Action=DescribePhysicalConnections
    &Timestamp=2016-05-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
    &Version=2014-05-26
    &SignatureVersion=1.0
    &Signature=XXXX%3D
    ```


