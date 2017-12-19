
### 发起一笔转账交易

创建并且向网络广播一笔转账交易

**请求语法**

```
POST /transaction/prepare-announce
```

**请求参数**

交易参数

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|timeStamp|Integer|是|从创建创世块到现在过去的秒数|
|amount|Integer|是|转账的金额|
|signature|Integer|是|交易签名|
|fee|Integer|是|转账费用，更高的费用意味着更高的转账优先级|
|recipient|String|是|接收方地址|
|type|Integer|是|转账类型|
|deadline|Integer|是|转账的有效时间。从创建创世块到失效时间过去的秒数，如果在有效时间内，该交易没有被包含近区块，则该交易被删除|
|payload|String|否|消息内容，大小为1KB|
|type|Integer|是|交易类型。1为非加密消息。2为加密消息|
|version|Integer|是|交易的版本。测试网络：-1744830462=0x98000002 正式网络：1744830466=0x68000002 Mijin网络：1610612738=0x60000002 |
|signer|String|是|交易创建者的公匙|
|mosaics|String|否|包含马赛克的数组|

马赛克参数

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|namespaceId|String|是|该马赛克对应的命名空间id|
|name|String|是|马赛克定义的名称|
|quantity|Integer|是|马赛克数量。数量总是马赛克的最小单位|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|type|Integer|响应类型|
|code|String|响应编码|
|message|String|响应消息|
|transactionHash|String||
|innerTransactionHash|String||

**请求示例**

```
{
        "transaction":
        {
            "timeStamp": 9111526,
            "amount": 3000000,
            "fee": 30000000,
            "recipient": "TBOBBSXX7BESJXDWGLP5Z7FM5HSTKUH5WIMPW562",
            "type": 257,
            "deadline": 9154726,
            "message":
            {
                "payload": "",
                "type": 1
            },
            "version": -1744830462,
            "signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
            "mosaics":[{
                "mosaicId":{
                    "namespaceId": "makoto.metals.silver",
                    "name": "coin"
                },
                "quantity": 1
            },{
                "mosaicId":{
                    "namespaceId": "nem",
                    "name": "xem"
                },
                "quantity": 100000000
            }]
        },
        "privateKey": "00983bb01d05edecfaef55df9486c111abb6299c754a002069b1d0ef4537441bda"
}
```

**返回示例**

```
{
        "type": 1,
        "code": 1,
        "message": "SUCCESS",
        "transactionHash": {
            "data":"c1786437336da077cd572a27710c40c378610e8d33880bcb7bdb0a42e3d35586"
        },
        "innerTransactionHash": {}
}
```
