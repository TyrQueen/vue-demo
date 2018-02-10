# Websocket练习

1. 你认为Websocket能解决哪些实际的问题，请至少列举三个实际场景？

>微博私信，新闻推送，排行榜变化，WebQQ，聊天室。

2. 如果现在要实现一个评论消息通知功能，比如说我在一个文章下写下了评论，文章作者能立刻（比如5s内）在消息中心收到提示如下图。
![](https://user-gold-cdn.xitu.io/2018/2/8/16174ca5e985ef8d?w=53&h=51&f=png&s=1819)
使用轮询(比如每5s发起一个http请求询问服务器是否有新消息)和Websocket都能实现，两者的优缺点是什么。


>轮询：</br>
优点：后台程序编写简单;</br>
缺点：轮询交互的实时性较低，浪费带宽和服务器资源，效率低，不太适用于客户端数量太多的情况。


>Websocket：</br>
优点：客户端与服务器建立的是 持久连接，服务器可以主动推送消息给客户端；只需要一次HTTP 握手，整个通讯过程是建立在一次连接状态中，server 端会一直推送消息更新反馈到客户端，直到客户端关闭请求;</br>
缺点：对开发者要求高了许多，难度增大;不兼容低版本的IE。


3. Websocket和Http有什么关系？(Hint: 101)


>WebSocket是基于HTTP的功能追加协议。为了实现WebSocket通信，首先需要客户端发起一次普通HTTP请求，服务器端在确认请求后，应返回状态码为101 Switching Protocols的响应。验证通过后，这个握手响应就确立了WebSocket连接，此后，服务器端就可以主动发信息给客户端了。


4. 简单的实现一个简单的发布订阅者模式。
```Javascript
var Emitter = function() {
    //...
    //此题不会...
}
Emitter.prototype.emit = null
Emitter.prototype.on = null;

// test part
var emitter = new Emitter()
emitter.on('keke', () => {
    console.log('receved keke');
})
emitter.emit('keke');
```

---
## Vue客户端选修
1. 你认为该如何在基于Vue的架构下为项目接入Websocket，当然不可能每个需要用到Websocket的组件都去new一个Websocket？

>可以用router-view。</br>
>1.main.vue中建立和服务器的连接；</br>
>2.将数据放入vuex；

2. 使用Websocket API实现一个简单的Websocket客户端并连接ws://121.40.165.18:8088，并发送“Wuanlife”消息。

```Javascript
var socket = new WebSocket("ws://121.40.165.18:8088");

socket.onopen = function(evt) {
    console.log("WebSocket open ...");
    socket.send("Wuanlife!");
};

socket.onmessage = function(evt) {
    var data = evt.data;
    console.log(evt.data);
    socket.close();
};

socket.onerror = function(evt) {
    console.log("WebSocket error.");
};

socket.onclose = function(evt) {
    console.log("WebSocket closed.");
};
```
运行结果：

![WebSocketConsole](https://tyrqueen.github.io/vue-demo/WebSocketConsle.png)

---
## NodeJS服务器端选修
1. 如果是类似午安网这种基于Access-Token的身份认证架构，怎么实现用户连接Websocket服务器的时候服务器能识别出接入的用户是谁？

```Javascript
wss.on('connection', (ws) => {
  ws.id = uuid();
});

```
2. 为什么Websocket服务器需要心跳检测？Websocket相关的心跳检测用来做什么？

>WebSocket服务器经常自动断开连接；断线重连