###  创建账户

**请求语法**

```
GET /account/generate
```

**响应报文**

```
{
    "privateKey": <Private Key>,
    "address": "Address",
    "publicKey": "Public key"
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
