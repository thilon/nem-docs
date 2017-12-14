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
