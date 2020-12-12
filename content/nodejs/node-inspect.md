% nodejs 调试

## 1. 查看node版本
```bash
node -v
```

## 2. 列出可用的node版本
```bash
nvm ls
```

## 3. 选择高版本node
```bash
nvm use 8.9.1
```

## 4. 以调试模式运行
```bash
// NODE_ENV=production node --inspect server.js

NODE_ENV=production node --inspect=0.0.0.0:9229 server.js
```
## 5. 查看调试信息
浏览器打开如下链接
http://host:port/json/list

1. e.g. http://172.20.12.12:9229/json/list

2. 信息内容
```json
[ {
  "description": "node.js instance",
  "devtoolsFrontendUrl": "chrome-devtools://devtools/bundled/inspector.html?experiments=true&v8only=true&ws=172.20.12.12:9229/29fe3b0e-9c15-4c21-9228-8f98279dfe7b",
  "faviconUrl": "https://nodejs.org/static/favicon.ico",
  "id": "29fe3b0e-9c15-4c21-9228-8f98279dfe7b",
  "title": "server.js",
  "type": "node",
  "url": "file:///root/yyumif/client/common/umif/server.js",
  "webSocketDebuggerUrl": "ws://172.20.12.12:9229/29fe3b0e-9c15-4c21-9228-8f98279dfe7b"
} ]

```

## 7. 将devtoolsFrontendUrl的值用浏览器打开


[node调试文档](https://nodejs.org/en/docs/guides/debugging-getting-started/)


