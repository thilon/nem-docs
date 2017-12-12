###  创建账户

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

**示例**

```
http://127.0.0.1:7890/account/generate
{
    "privateKey": "0962c6505d02123c40e858ff8ef21e2b7b5466be12c4770e3bf557aae828390f",
    "address": "NCKMNCU3STBWBR7E3XD2LR7WSIXF5IVJIDBHBZQT",
    "publicKey": "c2e19751291d01140e62ece9ee3923120766c6302e1099b04014fe1009bc89d3"
}
```

### 获取账户信息

**请求语法**

```
GET /account/get/<address>
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

**示例**

```
http://127.0.0.1:7890/account/get?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS
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
