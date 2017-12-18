### 获取节点基本信息

**请求语法**

```
GET /node/info
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|features|Integer|节点含有的特征数量，目前为1|
|networkId|Integer|主网络为：104(0x68),测试网络为：152(0x98)|
|application|String|该运行节点的应用名称|
|version|String|应用的版本号|
|platform|String|底层平台(OS,Java版本)|
|protocol|String|通讯协议(HTTP,HTTPS)|
|port|Integer|端口号|
|host|String|IP地址|
|name|String|节点名称|
|public-key|String|标识节点的公匙|

**请求示例**

```
http://127.0.0.1:7890/node/info
```

**响应示例**

```
{
  "metaData":
  {
    "features": 1,
    "application": "NIS",
    "networkId":104,
    "version": "0.4.33-BETA",
    "platform": "Oracle Corporation (1.8.0_25) on Windows 8"
   },
   "endpoint":
   {
      "protocol": "http",
      "port": 7890,
      "host": "81.224.224.156"
   },
   "identity":
   {
      "name": "Alice",
      "public-key": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
   }
}
```

### 获取节点扩展信息

**请求语法**

```
GET /node/extended-info
```

**请求参数**

无

**响应参数**

节点(Node)信息

|参数|类型|说明|
|:---|:---|:---|
|application|String|该运行节点的应用名称|
|version|String|应用的版本号|
|platform|String|底层平台(OS,Java版本)|
|protocol|String|通讯协议(HTTP,HTTPS)|
|port|Integer|端口号|
|host|String|IP地址|
|name|String|节点名称|
|public-key|String|标识节点的公匙|

NIS信息

|参数|类型|说明|
|:---|:---|:---|
|currentTime|Integer|NIS当前时间|
|application|String|该NIS的应用名称|
|startTime|Integer|该NIS的开始时间|
|version|String|NIS的版本号|
|signer|String|NIS的证书所使用的签名|

**请求示例**

```
http://127.0.0.1:7890/node/extended-info
```

**响应示例**

```
{
       "node": {
              "metaData":
              {
                     "application": "NIS",
                     "version": "0.4.33-BETA",
                     "platform": "Oracle Corporation (1.8.0_25) on Windows 8"
              },
              "endpoint":
              {
                     "protocol": "http",
                     "port": 7890,
                     "host": "81.224.224.156"
              },
              "identity":
              {
                     "name": "Alice",
                     "public-key": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
              }
       },
       "nisInfo":
       {
              "currentTime": 9288341,
              "application": "NEM Infrastructure Server",
              "startTime": 9238484,
              "version": "0.4.33-BETA",
              "signer": "CN=VeriSign Class 3 Code Signing 2010 CA,OU=Terms of use at https://www.verisign.com/rpa (c)10,OU=VeriSign Trust Network,O=VeriSign\\, Inc.,C=US"
       }
}
```

### 获取节点周边已知的节点

**请求语法**

```
GET /node/peer-list/all
```

**请求参数**

无

**响应参数**

节点(Node)信息

|参数|类型|说明|
|:---|:---|:---|
|application|String|该运行节点的应用名称|
|version|String|应用的版本号|
|platform|String|底层平台(OS,Java版本)|
|protocol|String|通讯协议(HTTP,HTTPS)|
|port|Integer|端口号|
|host|String|IP地址|
|name|String|节点名称|
|public-key|String|标识节点的公匙|

NIS信息

|参数|类型|说明|
|:---|:---|:---|
|inactive|Array|无法建立连接的节点集合|
|active|Array|能够建立连接并且远程节点及时响应的节点集合|
|busy|Array|能够建立连接，但是节点在超时到来前无法提供信息的节点集合|
|failure|Array|试图建立连接或节点无法正确验证自己时会发生致命错误的节点集合|
|data|Array|表示节点集合的通用状态只列出节点而不说关于节点状态的任何内容|

**请求示例**

```
http://127.0.0.1:7890/node/peer-list/all
```

**响应示例**

```
{
       "inactive": [
              <Node>,
              <Node>
       ],
       "active": [
              <Node>,
              <Node>
       ],
       "busy": [
              <Node>,
              <Node>
       ],
       "failure": [
              <Node>,
              <Node>
       ]
}
```

### 获取节点周边状态为'Active'的节点

**请求语法**

```
GET /node/peer-list/reachable
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|application|String|该运行节点的应用名称|
|version|String|应用的版本号|
|platform|String|底层平台(OS,Java版本)|
|protocol|String|通讯协议(HTTP,HTTPS)|
|port|Integer|端口号|
|host|String|IP地址|
|name|String|节点名称|
|public-key|String|标识节点的公匙|

**请求示例**

```
http://127.0.0.1:7890/node/peer-list/reachable
```

**响应示例**

```
{
       "data": [
              "metaData":
              {
                     "application": "NIS",
                     "version": "0.4.33-BETA",
                     "platform": "Oracle Corporation (1.8.0_25) on Windows 8"
              },
              "endpoint":
              {
                     "protocol": "http",
                     "port": 7890,
                     "host": "81.224.224.156"
              },
              "identity":
              {
                     "name": "Alice",
                     "public-key": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
              }
       ]
}
```

### 获取节点周边被选为可'广播'的节点

**请求语法**

```
GET /node/peer-list/active
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|application|String|该运行节点的应用名称|
|version|String|应用的版本号|
|platform|String|底层平台(OS,Java版本)|
|protocol|String|通讯协议(HTTP,HTTPS)|
|port|Integer|端口号|
|host|String|IP地址|
|name|String|节点名称|
|public-key|String|标识节点的公匙|

**请求示例**

```
http://127.0.0.1:7890/node/peer-list/active
```

**响应示例**

```
{
       "data": [
              "metaData":
              {
                     "application": "NIS",
                     "version": "0.4.33-BETA",
                     "platform": "Oracle Corporation (1.8.0_25) on Windows 8"
              },
              "endpoint":
              {
                     "protocol": "http",
                     "port": 7890,
                     "host": "81.224.224.156"
              },
              "identity":
              {
                     "name": "Alice",
                     "public-key": "a1aaca6c17a24252e674d155713cdf55996ad00175be4af02a20c67b59f9fe8a"
              }
       ]
}
```

### 获取节点周边被选为可'广播'节点中最高的区块链高度

**请求语法**

```
GET /node/active-peers/max-chain-height
```

**请求参数**

无

**响应参数**

|参数|类型|说明|
|:---|:---|:---|
|height|Integer|区块高度|

**请求示例**

```
http://127.0.0.1:7890/node/active-peers/max-chain-height
```

**响应示例**

```
{
  "height": 43920
}
```
