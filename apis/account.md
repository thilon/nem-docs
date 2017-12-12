### 创建账户

**请求语法**

```
GET /account/generate
```

**响应报文**

```
{
    "privateKey": <Private Key>,
    "address": <Address>,
    "publicKey": <Public key>
}
```

**请求示例**

```
http://127.0.0.1:7890/account/generate
```

**返回格式**

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

**响应报文**

```
{
    "account":
    {
        "address": <Address>,
        "balance": <Balance>,
        "vestedBalance": <Vested Balance>,
        "importance": <POI>,
        "publicKey": <Public Key>,
        "label": <null>,
        "harvestedBlocks": <Harvested blocks>
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": <Account status>,
        "remoteStatus": <Remote node status>
    }
}
```

**请求示例**

```
http://127.0.0.1:7890/account/get?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS
```

**返回格式**

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

**响应报文**

```
{
    "account":
    {
        "address": <Address>,
        "balance": <Balance>,
        "vestedBalance": <Vested Balance>,
        "importance": <POI>,
        "publicKey": <Public Key>,
        "label": <null>,
        "harvestedBlocks": <Harvested blocks>
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": <Account status>,
        "remoteStatus": <Remote node status>
    }
}
```

**请求示例**

```
http://127.0.0.1:7890/account/get/from-public-key?publicKey=f9bd190dd0c364261f5c8a74870cc7f7374e631352293c62ecc437657e5de2cd
```

**返回格式**

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

**响应报文**

```
{
    "account":
    {
        "address": <Address>,
        "balance": <Balance>,
        "vestedBalance": <Vested Balance>,
        "importance": <POI>,
        "publicKey": <Public Key>,
        "label": <null>,
        "harvestedBlocks": <Harvested blocks>
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": <Account status>,
        "remoteStatus": <Remote node status>
    }
}
```

**请求示例**

```
http://127.0.0.1:7890/account/get/forwarded?address=NC2ZQKEFQIL3JZEOB2OZPWXWPOR6LKYHIROCR7PK
```

**返回格式**

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

**响应报文**

```
{
    "account":
    {
        "address": <Address>,
        "balance": <Balance>,
        "vestedBalance": <Vested Balance>,
        "importance": <POI>,
        "publicKey": <Public Key>,
        "label": <null>,
        "harvestedBlocks": <Harvested blocks>
    },
    "meta":
    {
        "cosignatoryOf": [ ],
        "cosignatories": [ ],
        "status": <Account status>,
        "remoteStatus": <Remote node status>
    }
}
```

**请求示例**

```
http://127.0.0.1:7890/account/get/forwarded/from-public-key?publicKey=bdd8dd702acb3d88daf188be8d6d9c54b3a29a32561a068b25d2261b2b2b7f02
```

**返回格式**

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
