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

**返回参数**

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

**返回参数**

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

**返回参数**

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
