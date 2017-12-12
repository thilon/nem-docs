### 请求接口

**服务端口**

>主网络端口号为7890

**通信协议**

支持通过HTTP方式进行请求通信

 **请求方法**
 
 支持 HTTP GET 方法发送请求，这种方式下请求参数需要包含在请求的 URL 中。并可在浏览器中直接执行
 支持 HTTP POST 方法发送请求，这种方式无法在浏览器中直接调用。并通过在请求体中的JSON格式与服务器端通信
 
 **请求格式**
 
 http://127.0.0.1:7890<path to API request>?<parameters>
 
 ```
 请求示例
 http://127.0.0.1:7890/account/get?address=TALICELCD3XPH4FFI5STGGNSNSWPOTG5E4DS2TOS
 ```
 
