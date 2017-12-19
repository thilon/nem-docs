### 获取根命名空间

获取根命名空间。请求支持分页，即批量检索指定大小的根命名空间

**请求语法**

```
GET /namespace/roots?id=<id>&pageSize=<pageSize>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|id|Integer|否|如果不提供则返回最近租用的根命名空间|
|pagesize|Integer|否|每个请求返回的马赛克定义数量。默认值为25。最小值为5，最大值为100|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|id|String|命名空间id|
|fqn|String|命名空间的完全限定名，即命名空间id|
|owner|String|命名空间拥有者地址|
|height|Integer|所有权开始的高度|

**请求示例**

```
http://127.0.0.1:7890/namespace/roots?id=26754&pageSize=35
```

**返回示例**

```
{
        "data": [{
            "meta": {
                "id": 26264
            },
            "namespace": {
                "fqn": "makoto.metal.coins",
                "owner": "TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH",
                "height": 13465
            }
        },{
            "meta": {
                "id": 25421
            },
            "namespace": {
                "fqn": "gimre.vouchers",
                "owner": "TDGIMREMR5NSRFUOMPI5OOHLDATCABNPC5ID2SVA",
                "height": 12392
            }
        }]
}
```

### 获取一个指定的命名空间

根据给定的id获取一个命名空间

**请求语法**

```
GET /namespace?namespace=<namespace id>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|namespace|String|是|命名空间id|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|fqn|String|命名空间的完全限定名，即命名空间id|
|owner|String|命名空间拥有者地址|
|height|Integer|所有权开始的高度|

**请求示例**

```
http://127.0.0.1:7890/namespace?namespace=makoto.metal.coins
```

**返回示例**

```
{
        "fqn": "makoto.metal.coins",
        "owner": "TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH",
        "height": 13465
}
```

### 获取马赛克定义

从给定的命名空间获取马赛克定义。请求支持分页。该请求返回一个数组

**请求语法**

```
GET /namespace/mosaic/definition/page?namespace=<namespace id>&id=<id>&pageSize=<pageSize>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|namespace|String|是|命名空间id|
|id|String|否||
|pagesize|Integer|否|每个请求返回的马赛克定义数量。默认值为25。最小值为5，最大值为100|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|id|Integer|马赛克定义id|
|creator|String|马赛克定义创建者的公匙|
|namespaceId|String|命名空间id|
|properties|-|马赛克属性值|

**请求示例**

```
http://127.0.0.1:7890/namespace/mosaic/definition/page?namespace=makoto.metal.coins
```

**返回示例**

```
{
    "data": [{
        "meta": {
            "id": 3541
        },
        "mosaic": {
            "creator": "10cfe522fe23c015b8ab24ef6a0c32c5de78eb55b2152ed07b6a092121187100",
            "id": {
                "namespaceId": "makoto.metal.coins",
                "name": "silver coin"
            },
            "description": "Real silver coins, pure silver",
            "properties": [{
                 "name": "divisibility",
                 "value": "0"
            },{
                "name": "initialSupply",
                "value": "1000"
            },{
                "name": "supplyMutable",
                "value": "false"
            },{
                "name": "transferable",
                "value": "true"
            }]
        }
    }]
}
```
