### 获取区块链高度

**请求语法**

```
GET /chain/height
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|height|Integer|区块链高度|

**请求示例**

```
http://127.0.0.1:7890/chain/height
```

**返回示例**

```
{
  "height": 42799
}
```

### 获取区块链分值

**请求语法**

```
GET /chain/score
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|score|String|区块链分数值是一个大于等于0的整形值，得分越高，区块链越健康，在同步过程中，节点试图在网络中获得最佳的链。该值以十六进制表示|

**请求示例**

```
http://127.0.0.1:7890/chain/score
```

**返回示例**

```
{
  "score": "18722d5a7d590deb"
}
```

### 获取区块链的最后一个区块

**请求语法**

```
GET /chain/last-block
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|timeStamp|Integer|区块的创建时间|
|signature|String|区块的签名。链中的区块又创建者签名|
|prevBlockHash|String|上一个区块的sha3-256Hash值|
|data|String||
|type|Integer|区块类型。目前默认值为1，表示一个常规的区块|
|transactions|Array|交易数组，保存了一组交易|
|version|Integer|区块的版本号，4字节整形。主网络为：1744830465(0x68 << 24 + 1),测试网络为：-1744830463(0x98 << 24 + 1)|
|signer|String|区块创建者的公匙，十六进制字符串|
|height|Integer|区块的高度，每个区块都拥有一个唯一的高度值，随后的区块在高度上都相差1|

**请求示例**

```
http://127.0.0.1:7890/chain/last-block
```

**返回示例**

```
{
        "timeStamp": 9232968,
        "signature": "0a1351ef3e9b19c601e804a6d329c9ade662051d1da2c12c3aec9934353e421c79de7d8e59b127a8ca9b9d764e3ca67daefcf1952f71bc36f747c8a738036b05",
        "prevBlockHash": {
        "data": "58efa578aea719b644e8d7c731852bb26d8505257e03a897c8102e8c894a99d6"
        },
        "type": 1,
        "transactions": [
        ],
        "version": 1744830465,
        "signer": "2afca04d2cb8d16cf3656274bc55b95e60be823cfb7230d82f791ed42a309ee7",
        "height": 42804
}
```

### 通过区块hash值获取一个区块

**请求语法**

```
GET /block/get?blockHash=<block hash>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|blockHash|String|是|区块的Hash值|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|timeStamp|Integer|区块的创建时间|
|signature|String|区块的签名。链中的区块又创建者签名|
|prevBlockHash|String|上一个区块的sha3-256Hash值|
|data|String||
|type|Integer|区块类型。目前默认值为1，表示一个常规的区块|
|transactions|Array|交易数组，保存了一组交易|
|version|Integer|区块的版本号，4字节整形。主网络为：1744830465(0x68 << 24 + 1),测试网络为：-1744830463(0x98 << 24 + 1)|
|signer|String|区块创建者的公匙，十六进制字符串|
|height|Integer|区块的高度，每个区块都拥有一个唯一的高度值，随后的区块在高度上都相差1|

**请求示例**

```
http://127.0.0.1:7890/block/get?blockHash=58efa578aea719b644e8d7c731852bb26d8505257e03a897c8102e8c894a99d6
```

**返回示例**

```
{
        "timeStamp": 9232942,
        "signature": "005f91b8908fc173a428ff8e8c4a0ee0d69e4004aed0d08f27690b6b6672ef74ccc6b89695bed5f29b0f4a812cb84bfa459f52a4e14a11e574793969f0e1a30f",
        "prevBlockHash": {
        "data": "f721e563b4431594c5af6f6be0a913f47f0aca6c3b8ee6a703bfe175ee54babf"
        },
        "type": 1,
        "transactions": [
        ],
        "version": 1744830465,
        "signer": "78e121cc1cf63424651ec64251e78efda81386c9f5e9eb4cb08b2a2192c9dce5",
        "height": 42803
}
```

### 通过区块高度获取一个区块

**请求语法**

```
POST /block/at/public
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|blockHeight|Integer|是|JSON格式的区块链高度|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|timeStamp|Integer|区块的创建时间|
|signature|String|区块的签名。链中的区块又创建者签名|
|prevBlockHash|String|上一个区块的sha3-256Hash值|
|data|String||
|type|Integer|区块类型。目前默认值为1，表示一个常规的区块|
|transactions|Array|交易数组，保存了一组交易|
|version|Integer|区块的版本号，4字节整形。主网络为：1744830465(0x68 << 24 + 1),测试网络为：-1744830463(0x98 << 24 + 1)|
|signer|String|区块创建者的公匙，十六进制字符串|
|height|Integer|区块的高度，每个区块都拥有一个唯一的高度值，随后的区块在高度上都相差1|

**请求示例**

```
{
  "height": 2649
}
```

**返回示例**

```
{
        "timeStamp": 9232942,
        "signature": "005f91b8908fc173a428ff8e8c4a0ee0d69e4004aed0d08f27690b6b6672ef74ccc6b89695bed5f29b0f4a812cb84bfa459f52a4e14a11e574793969f0e1a30f",
        "prevBlockHash": {
        "data": "f721e563b4431594c5af6f6be0a913f47f0aca6c3b8ee6a703bfe175ee54babf"
        },
        "type": 1,
        "transactions": [
        ],
        "version": -1744830463,
        "signer": "78e121cc1cf63424651ec64251e78efda81386c9f5e9eb4cb08b2a2192c9dce5",
        "height": 42803
}
```

### 获取一组区块

**请求语法**

```
POST /local/chain/blocks-after
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|blockHeight|Integer|是|JSON格式的区块链高度。最多获取该高度之后的10个区块|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|txes|Array|一个区块中包含的一组交易|
|block|String|区块信息|
|hash|String|上一个区块的sha3-256Hash值|

**请求示例**

```
{
  "height": 2649
}
```

**返回示例**

```
{
  "data":[{
    "txes":[{
      "tx": <ExplorerViewModelTransaction>
      "tx": <ExplorerViewModelTransaction>
    }],
    "block": <Block>
    "hash":"8ca8a3e01ac0eb482e668fda74141984ba118b027fc5f1f67d2d36a38bf48c49"
 }]
}
```
