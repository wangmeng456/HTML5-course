# 数据通信
## Web中传统数据通信方式的缺陷
* HTTP 协议

  一种无状态的、无连接的、单向的应用层协议。

  采用了请求/响应模型，Request = Response 。

  通信请求只能由客户端发起，服务端对请求做出应答处理。
* Ajax 

  由JavaScript发起请求，局部更新页面/应用。
## 让网页实时通信（WebSocket）
* WebSocket 原理
  
  浏览器和服务器只需要做一个握手的动作，便形成了一条快速通道。两者之间就直接可以数据互相传送。
* WebSocket、HTTP与TCP

  WebSocket和HTTP属于应用层协议，都是通过TCP协议传输数据
  
  WebSocket是全双工通信协议，HTTP是单向的通信协议
  
  对于WebSocket来说，它必须依赖HTTP协议进行一次握手，握手成功后，数据就直接从TCP通道传输，此后就与HTTP无关了
* WebSocket特点

  （1）建立在 TCP 协议之上，服务器端的实现比较容易。
  
  （2）与 HTTP 协议有着良好的兼容性。默认端口也是80和443，握手阶段采用 HTTP 协议，不容易屏蔽，能通过各种 HTTP 代理服务器。
  
  （3）数据格式比较轻量，性能开销小，通信高效。
  
  （4）可以发送文本，也可以发送二进制数据。
  
  （5）没有同源限制，客户端可以与任意服务器通信。
  
  （6）协议标识符是ws（如果加密，则为wss），服务器网址就是 URL。
* WebSocket意义

  WebSocket 是HTML5中最强大的通信功能，仅通过一个Socket就可以进行通信，不仅是对常规HTTP通信的一种增量加强，它更代表着一次巨大的进步，对实时的、事件驱动的Web应用程序更是如此。	
  
  有了WebSocket以后：数据双向实时传输。在Web中轻松实现：网游、在线聊天；股票、位置监控…
## WebSocket客户端
* WebSocket 构造函数
  ```
  var Socket = new WebSocket(url, [protocol] );
  ```
* WebSocket属性
  ```
  switch (ws.readyState) {
      case WebSocket.CONNECTING:  // 值为0，表示正在连接
        // do something
        break;
      case WebSocket.OPEN:       // 值为1，表示连接成功，可以通信了
        // do something
        break;
      case WebSocket.CLOSING:   // 值为2，表示连接正在关闭
        // do something
        break;
      case WebSocket.CLOSED:    // 值为3，表示连接已经关闭，或者打开连接失败
        // do something
        break;
      default:
        // this never happens
        break;
  } 
  ```
  ```
  // WebSocket.bufferedAmount  // 表示已被 send() 放入正在队列中等待传输，但是还没有发出二进制数据
  var socket = new WebSocket(url, [protocol] );
  var data = new ArrayBuffer(10000000);
  socket.send(data);
  if (socket.bufferedAmount === 0) {
    // 发送完毕
  } 
  else {
    // 发送还没结束
  }
  ```
* WebSocket事件
  ```
  var ws = new WebSocket('ws://localhost:8080');
  
  ws.addEventListener('open', function (event) {
      ws.send('Hello Server!');
  });
  
  // window.WebSocket.onopen     // 实例对象的onopen属性，用于指定连接成功后的回调函数
  ws.onopen = function () {
      ws.send('Hello Server!');
  }
  
  // window.WebSocket.onmessage  // 实例对象的onmessage属性，用于指定收到服务器数据后的回调函数
  ws.onmessage = function(event) {
      var data = event.data;
      // 处理数据
  };
  
  // window.WebSocket.onclose    // 实例对象的onclose属性，用于指定连接关闭后的回调函数
  ws.onclose = function(event) {
      var code = event.code;
      var reason = event.reason;
      var wasClean = event.wasClean;
      // handle close event
  };
  ```
* WebSocket方法
  ```
  // window.WebSocket.send()    // 实例对象的send()方法用于向服务器发送数据
  
  // window.WebSocket.close()   // 实例对象的close()方法用于关闭连接
  ```
* 使用WebSocket
  ```
  // 设定 WebSocket 服务器地址
  var url = "ws://localhost:8888";
  // 建立 WebSocket 连接，返回连接的 WebSocket 对象
  var ws = new WebSocket(url);
  // 连接事件
  ws.onopen = function(){
     console.log("Connection open");
  }
  // 消息事件
  ws.onmessage = function(e){
    // 事件对象的 data 属性保存了服务器传递来的具体数据
    console.log("Closed");
  }
  
  document.getElementById("sendButton").onClick = function(){
    // WebSocket 对象发送数据
    ws.send("Send Message");
  }
  ```
## WebSocket服务端
* 常用的 Node 实现有以下三种

  WebSockets
  
  Socket.IO
  
  WebSocket-Node












