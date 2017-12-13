### 获取服务器心跳

**响应类型**

|type|描述|
|:---|:---|
|1|响应类型的类型是一种验证|
|2|响应结果的类型是服务器心跳|
|4|响应结果的类型是服务器状态|

**请求语法**

```
GET /heartbeat
```

**请求参数**
无

**响应参数**

type为2时的响应码

|响应码|描述|
|:---|:---|
|1|Successful heart beat detected|

**请求示例**

```
http://127.0.0.1:7890/heartbeat
```

**返回示例**

>JSON格式

```
{
  "code": 1,
  "type": 2,
  "message": "ok"
}
```

### 获取服务器状态

**请求语法**

```
GET /status
```

**请求参数**
无

**响应报文**

```
{
  "code": <Code>,
  "type": 4,
  "message": <Message>
}
```

**响应参数**

type为4时的响应码

|响应码|描述|
|:---|:---|
|0|Unknown status|
|1|NIS is stopped|
|2|NIS is starting|
|3|NIS is running|
|4|NIS is booting the local node (implies NIS is running)|
|5|The local node is booted (implies NIS is running)|
|6|The local node is synchronized (implies NIS is running and the local node is booted)|
|7|NIS local node does not see any remote NIS node (implies running and booted)|
|8|NIS is currently loading the block chain from the database. In this state NIS cannot serve any requests|

**请求示例**

```
http://127.0.0.1:7890/status
```

**返回示例**

>JSON格式

```
{
  "code": 6,
  "type": 4,
  "message": "status"
}
```
