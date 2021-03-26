![npm version](https://img.shields.io/badge/npm-1.0.0-brightgreen)
 > SSocket + SServer  WebSocket  + 简易分布式消息服务，服务对象继承于 Ssocket 项目对象，支持所有方法 觉得小弟写的还行的话，就给个[Star](https://github.com/mytwz/ssocket-sserver-node)⭐️吧~

## 食用说明

### [安装启动中心服务器](https://github.com/mytwz/network-node-szook)
### [点击安装客户端程序](https://github.com/mytwz/ssocket-js)

```javascript

const http = require("http")
const WebSocekt = require("../");
const app = new WebSocekt({
    server: http.createServer(),
    verifyClient: ({ origin, secure, req }, callback) => {
        callback(true/**返回 false 的话，连接就会中断并给前端返回 403 的HTTP错误码 */)
    }, // 非必传
    perMessageDeflate: true, // 非必传
    maxPayload: 1024 * 1024 * 10, // 最大传输单位 10M // 非必传
    /**本地网络Ip */
    ip: "10.9.16.24",
    /**WebSocket 端口号 */
    websocket_port: 8082,
    /**分布式消息服务的 端口号 */
    sserver_port: 8081,
    /**入网用户名 */
    username: "summer",
    /**入网帐号密码 */
    password: "summer",
    /**与中心服务器通信的签名Key */
    signKey: "signKey",
    /**中心服务地址 */
    centralUrl: "http://10.9.16.24:8080"
})

app.start(function () {
    console.log("启动成功")
})


```