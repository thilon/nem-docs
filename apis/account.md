### 创建账户

**请求语法**

```
GET /account/generate
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|privateKey|String|返回新创建账户的私匙|
|address|String|返回新创建账户的地址|
|publicKey|String|返回新创建账户的公匙|

**请求示例**

```
http://127.0.0.1:7890/account/generate
```

**返回示例**

>JSON格式

```
{
    "privateKey": "0962c6505d02123c40e858ff8ef21e2b7b5466be12c4770e3bf557aae828390f",
    "address": "NCKMNCU3STBWBR7E3XD2LR7WSIXF5IVJIDBHBZQT",
    "publicKey": "c2e19751291d01140e62ece9ee3923120766c6302e1099b04014fe1009bc89d3"
}
```

### 通过地址获取账户信息

**请求语法**

```
GET /account/get?address=<address>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|查询账户的地址|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|address|String|账户的地址|
|balance|Double|账户的余额|
|vestedBalance|Double|账户的归属余额|
|importance|Double|账户的重要性值|
|publicKey|String|账户的公匙|
|label|String|null|
|harvestedBlocks|Integer|收获的块数量|
|cosignatoryOf|||
|cosignatories|||
|status|String|该账号状态|
|remoteStatus|String|远程节点状态|

**请求示例**

```
http://127.0.0.1:7890/account/get?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS
```

**返回示例**

>JSON格式

```
{
    "account":
    {
        "address": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "balance": 124446551689680,
        "vestedBalance": 104443451691625,
        "importance": 0.010263666447108395,
        "publicKey": "a11a1a6c17a24252e674d151713cdf51991ad101751e4af02a20c61b59f1fe1a",
        "label": null,
        "harvestedBlocks": 645
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": "LOCKED",
        "remoteStatus": "ACTIVE"
    }
}
```

### 通过公匙获取账户信息

**请求语法**

```
GET /account/get/from-public-key?publickey=<PublicKey>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|PublicKey|String|是|查询账户的公匙|

**响应参数**

同上

**请求示例**

```
http://127.0.0.1:7890/account/get/from-public-key?publicKey=f9bd190dd0c364261f5c8a74870cc7f7374e631352293c62ecc437657e5de2cd
```

**返回示例**

>JSON格式

```
{
    "account":
    {
        "address": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "balance": 124446551689680,
        "vestedBalance": 104443451691625,
        "importance": 0.010263666447108395,
        "publicKey": "a11a1a6c17a24252e674d151713cdf51991ad101751e4af02a20c61b59f1fe1a",
        "label": null,
        "harvestedBlocks": 645
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": "LOCKED",
        "remoteStatus": "ACTIVE"
    }
}
```

### 通过委托账号地址获取原始账户信息

**请求语法**

```
GET /account/get/forwarded?address=<address>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|委托账户的地址|

**响应参数**

同上

**请求示例**

```
http://127.0.0.1:7890/account/get/forwarded?address=NC2ZQKEFQIL3JZEOB2OZPWXWPOR6LKYHIROCR7PK
```

**返回示例**

>JSON格式

```
{
    "account":
    {
        "address": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "balance": 124446551689680,
        "vestedBalance": 104443451691625,
        "importance": 0.010263666447108395,
        "publicKey": "a11a1a6c17a24252e674d151713cdf51991ad101751e4af02a20c61b59f1fe1a",
        "label": null,
        "harvestedBlocks": 645
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": "LOCKED",
        "remoteStatus": "ACTIVE"
    }
}
```

### 通过委托账号公匙获取原始账户信息

**请求语法**

```
GET /account/get/forwarded/from-public-key?publickey=<delegate account publickey>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|publickey|String|是|委托账户的公匙|

**响应参数**

同上

**请求示例**

```
http://127.0.0.1:7890/account/get/forwarded/from-public-key?publicKey=bdd8dd702acb3d88daf188be8d6d9c54b3a29a32561a068b25d2261b2b2b7f02
```

**返回示例**

>JSON格式

```
{
    "account":
    {
        "address": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "balance": 124446551689680,
        "vestedBalance": 104443451691625,
        "importance": 0.010263666447108395,
        "publicKey": "a11a1a6c17a24252e674d151713cdf51991ad101751e4af02a20c61b59f1fe1a",
        "label": null,
        "harvestedBlocks": 645
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": "LOCKED",
        "remoteStatus": "ACTIVE"
    }
}
```

### 获取账户状态

**请求语法**

```
GET /account/status?address=<account address>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|cosignatoryOf|||
|status|String|该账号状态|
|remoteStatus|String|远程节点状态|

**请求示例**

```
http://127.0.0.1:7890/account/status?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS
```

**返回示例**

>JSON格式

```
{
    "cosignatoryOf": [ ],
    "status": "LOCKED",
    "remoteStatus": "ACTIVE"
}
```

### 获取账户转入的交易

**请求语法**

```
GET /account/transfers/incoming?address=<account address>&hash=<hash>&id=<id>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|
|hash|String|可选|交易的hash值，不填时将返回最新的交易，填写时返回该hash交易之前的交易，最多25笔交易|
|id|String|可选|交易的id值，不填时将返回最新的交易，填写时返回该id交易之前的交易，最多25笔交易|

!> 注意：hash和id不能同时出现

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|cosignatoryOf|||
|status|String|该账号状态|
|remoteStatus|String|远程节点状态|

**请求示例**

```
http://127.0.0.1:7890/account/transfers/incoming?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS&hash=949583a20ebdfdcb58277eb42fef3e66e9e6bbfc47304d8741a82c68f7c53a2
```

**返回示例**

>JSON格式

```
{
        "data": [
        {
        "meta":
        {
        "id": 71245,
        "height": 40706,
        "hash": {
        "data":"15c373ad4c3fe6af47d1941379ff262f785bdcfa07c02ac3608bc10da27d5e82"
        }
        },
        "transaction":
        {
        "timeStamp": 9106400,
        "amount": 1000000000,
        "signature": "449cd76ea8bda2220b3d6ad6f8db5f81d4e68ad3d4b0c3db9a3c267355657639eabed3dbcef8e0cc22953ae2b36a22ee7dc6327484c9649cccd686a511eca105",
        "fee": 3000000,
        "recipient": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "type": 257,
        "deadline": 9149600,
        "message":
        {
        "payload": "280000005444334b32493543524850595634425a5a5a4c335850454e4",
        "type": 2
        },
        "version": -1744830463,
        "signer": "c20a1dffe699c7a68328986273265e33fceebe074f274240ef890dd80ad55ed6"
        }
        },
        {
        "meta":
        {
        "id": 71356,
        "height": 40629,
        "hash": {
        "data":"37c34ead4c3fe6af42d994135798262f785ba2d807c02ac3608bc10da12e5f87"
        }
        },
        "transaction":
        {
        "timeStamp": 9101541,
        "amount": 49997995000000,
        "signature": "57c3c48d2ae8b24240b57d72493f498cfeb61e2ab87237dc0e08c51007d5c7f15847d0e08c0286e68a72028925db5fa809ca9d57e2cb6eebe11822176a834c0b",
        "fee": 2005000000,
        "recipient": "TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS",
        "type": 257,
        "deadline": 9144741,
        "message":
        {
        "payload": "526f6262657279212121",
        "type": 1
        },
        "version": -1744830463,
        "signer": "546e4fb9c81db84e04d8e9e67380db0fe1f540df09a527fb995b589b5695ae24"
        }
        }]
}
```

### 获取账户转出的交易

**请求语法**

```
GET /account/transfers/outgoing?address=<account address>&hash=<hash>&id=<id>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|
|hash|String|可选|交易的hash值，不填时将返回最新的交易，填写时返回该hash交易之前的交易，最多25笔交易|
|id|String|可选|交易的id值，不填时将返回最新的交易，填写时返回该id交易之前的交易，最多25笔交易|

!> 注意：hash和id不能同时出现

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|cosignatoryOf|||
|status|String|该账号状态|
|remoteStatus|String|远程节点状态|

**请求示例**

```
http://127.0.0.1:7890/account/transfers/outgoing?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS&hash=949583a20ebdfdcb58277eb42fef3e66e9e6bbfc47304d8741a82c68f7c53a22
```

**返回示例**

>JSON格式

```
{
        "data": [
        {
        "meta":
        {
        "id": 70498,
        "height": 40803,
        "hash": {
        "data":"37c34ead4c3fe6af42d994135798262f785ba2d807c02ac3608bc10da12e5f87"
        }
        },
        "transaction":
        {
        "timeStamp": 9111526,
        "amount": 1000000000,
        "signature": "651a19ccd09c1e0f8b25f6a0aac5825b0a20f158ca4e0d78f2abd904a3966b6e3599a47b9ff199a3a6e1152231116fa4639fec684a56909c22cbf6db66613901",
        "fee": 3000000,
        "recipient": "TDGIMREMR5NSRFUOMPI5OOHLDATCABNPC5ID2SVA",
        "type": 257,
        "deadline": 9154726,
        "message":
        {
        "payload": "74657374207472616e73616374696f6e",
        "type": 1
        },
        "version": -1744830463,
        "signer": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
        }
        }]
}
```

### 获取账户全部交易

**请求语法**

```
GET /account/transfers/all?address=<account address>&hash=<hash>&id=<id>
```
**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|
|hash|String|可选|交易的hash值，不填时将返回最新的交易，填写时返回该hash交易之前的交易，最多25笔交易|
|id|String|可选|交易的id值，不填时将返回最新的交易，填写时返回该id交易之前的交易，最多25笔交易|

!> 注意：hash和id不能同时出现

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|cosignatoryOf|||
|status|String|该账号状态|
|remoteStatus|String|远程节点状态|

**请求示例**

```
http://127.0.0.1:7890/account/transfers/all?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS&hash=949583a20ebdfdcb58277eb42fef3e66e9e6bbfc47304d8741a82c68f7c53a22
```

**返回示例**

同转出交易和转入交易

### 获取账户的全部命名空间

**请求语法**

```
GET /account/namespace/page?address=<account address>&parent=<parent namespace id>&id=<id>&pageSize=<page size>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|
|parent|String|可选|上级命名空间的id|
|id|Integer|可选||
|pageSize|Integer|可选|返回的命名空间数量|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|fqn|String|命名空间名称|
|owner|String|该命名空间的拥有账户地址|
|height|Integer|该命名空间所在的区块id|

**请求示例**

```
http://127.0.0.1:7890/account/namespace/page?address=TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH&parent=makoto.metal
```

**返回示例**

```
{
        "data": [{
        "fqn": "makoto.metal.coins",
        "owner": TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH",
        "height": 13465
        }]
}
```

### 获取账户创建的马赛克定义

**请求语法**

```
GET /account/mosaic/definition/page?address=<address>&parent=<parent namespace id>&id=<id>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|
|parent|String|可选|上级命名空间的id|
|id|Integer|可选| |

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|creator|String|命名空间名称|
|namespaceId|String|命名空间的id|
|name|Integer|命名空间的名称|
|divisibility|Integer|定义马赛克的可分性。如divisibility=3，表示一个马赛克可分割的最小值是0.001，即精确到小数点后3位|
|initialSupply|Integer|创建马赛克定义时，创建者可以指定一个初始供应值。初始供应值区间为(0,9000000000)，默认值是1000|
|supplyMutable|Boolean|创建者可以定义马赛克总量是否可以变动。值为"true"或"false",默认值为"false"|
|transferable|Boolean|马赛克是否可以在除创建者之外的帐户中转移。值为"true"或"false"。如果设置为“false”，则马赛克只能由创建者发送或接收；如果设置为“true”，则马赛克可以在任意账户中转移|

**请求示例**

```
http://127.0.0.1:7890/account/mosaic/definition/page?address=TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH&parent=makoto.metal.coins
```

**返回示例**

```
{
        "data": [{
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
        }]
}
```

### 获取账户拥有的马赛克

**请求语法**

```
GET /account/mosaic/owned?address=<address>
```

**请求参数**

|参数|类型|必填|说明|
|:---|:---|:---:|:---|
|address|String|是|账户地址|

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|namespaceId|String|马赛克所在的命名空间的id|
|name|Integer|马赛克所在的命名空间的名称|
|quantity|Integer|马赛克的数量|

**请求示例**

```
http://127.0.0.1:7890/account/mosaic/owned?address=TD3RXTHBLK6J3UD2BH2PXSOFLPWZOTR34WCG4HXH
```

**返回示例**

```
{
        "data": [{
        "mosaicId": {
        "namespaceId": "alice.drinks",
        "name": "orange juice"
        },
        "quantity": 123
        },{
        "mosaicId": {
        "namespaceId": "makoto.metal.coins",
        "name": "silver coin"
        },
        "quantity": 8
        }]
}
```
