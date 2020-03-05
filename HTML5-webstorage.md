# Web 存储
## 存储简介
### Cookie -- 保存用户信息、用户设置、密码记忆
* 包含的属性：

  name：表示 Cookie 的名称。
  
  expires：指定 Cookie 在删除之前要在用户的计算机上保留的时间。默认 Cookie 只对当前浏览器会话有效。
  
  path：决定 Cookie 对于服务器上的其他网页的可用性。
  
  domain：设置相同域的多台服务器共享一个 Cookie。
  
  secure：表示 Cookie 只能通过使用 HTTPS 或其他安全协议的 Internet 连接来运输。
* Cookie 的缺点：

  使用简单的文本存储数据，安全性差。保存在客户端浏览器，容易被黑客窃取。
  
  存储容量有限，只有 4KB 的存储空间。
  
  每次访问服务器，都会来回传送 Cookie ，浪费带宽，尤其是使用移动设备时。
  
  客户端操作 Cookie，非常复杂。
### HTML5 Web 存储简介
* HTML5 Web 存储的优点：
  
  存储空间更大，浏览器至少提供 5M 的空间。
  
  数据仅仅存储在本地，不会自动向服务器发送。
  
  提供丰富的接口，方便的操作数据。
  
  独立的存储空间，每个域都有各自存储空间，不会造成混乱。
### Web存储提供两种存储机制
* LocalStorage

  将数据保存在客户端本地的硬件设备中，即使浏览器被关闭了，该数据仍然存在，下次打开浏览器访问网站时仍然可以继续使用。
* SessionStorage

  将数据保存在session对象中。session 是指用户在浏览某个网站时，从进入网站到浏览器关闭所经过的这段时间。session 对象可以用来保存在这段时间内所要求保存的任何数据。当用户关闭浏览器窗口后，数据会被删除。
## LocalStorage 使用方法
* Web Storage用法

  存储是基于键/值对的形式存储的，每个键值对称为一个项（item）。存储和检索数据都是通过指定的键名。
  
  键名的类型是字符串类型。
  
  值可以是包括字符串、布尔值、数值在内的任意 JavaScript 类型。
  
  key:"view",value:"67"
* Web Storage API

  检测浏览器是否支持
  ```
  if(！window.localStorage) {
      alert(“浏览器不支持localstorage");
      return false;
  }
  else{
        //主逻辑业务
  }
  ```
  存储数据项
  ```
  localStorage.setItem(key, value)
  localStorage["key"] = value
	localStorage.key = value
  ```
  读取数据项
  ```
   localStorage.getItem(key)
   localStorage["key"] 
   localStorage.key
  ```
  删除数据项
  ```
  localStorage.removeItem(key)
  ```
  清除全部数据
  ```
  localStorage.clear( )
  ```
  获得键名
  ```
  localStorage.key(index)
  ```
  获得数据项的个数
  ```
  localStorage.length
  ```
* Web Storage 对象如何存储？---转换为字符串JSON,API
  ```
  var storage=window.localStorage;
  var data={
    name: 'zhangsan',
    hobby: 'study'
  };
  var d=JSON.stringify(data);    //将JSON转换成为JSON字符串
  storage.setItem("data",d);           
  var json=storage.getItem("data"); 
  var jsonObj=JSON.parse(json); //将字符串转换成为JSON对象
  console.log(typeof jsonObj);
  ```
## SessionStorage 使用方法
* 检测浏览器是否支持
  ```
  if(！window.sessionStorage) {
      alert(“浏览器不支持localstorage");
      return false;
  }
  else{
        //主逻辑业务
  }
  ```
* session 对象方法

  保存数据：sessionStorage.setItem(Key, value)
  
  读取数据：sessionStorage.getItem(Key)
  
  获得键名：sessionStorage.key(index)
  
  移除数据：sessionStorage.removeItem(key)
  
  清除所有数据：sessionStorage.clear()
## Web Storage 实例
* 使用 HTML5 存储技术实现一个简单的 Web 留言本。

使用文本域输入数据，单击“添加”按钮时，会将数据保存到 localStorage 中，在表单下面放置一个 P 元素来显示保存后的数据
```
// 第一步：编写显示页面用的HTML代码部分
// 点击“添加按钮”来保存数据，点击“全部清除”按钮来消除全部数据
<h1>简单Web留言本</h1>
<textarea id="memo" cols="60" rows="10"></textarea><br>
<input type="button" value="添加" onclick="saveStorage('memo'); "/>
<input type="button" value="全部清除" onclick="clearStorage('msg'); "/>
<hr/>
<p id="msg"></p>

// 第二步：编写点击“添加”按钮时调用的 saveStorage函数
// 在这个函数中使用“new Date().getTime()”语句得到了当前的日期和时间戳，然后调用localStorage.setItem 方法，将得到的时间戳作为键值，并将文本框中的数据作为键名进行保存
// 保存后，调用脚本中的 loadStorage 函数在页面上重新显示保存后的数据。

// 第三步：获取保存数据
// 使用 loadStorage.length 属性获取保存数据的条数，循环，从 0 开始将该变量作为 index 参数传入 loadStorage.key（index）属性，每次循环时该变量加 1，以此取得保存在 loadStorage中的所有数据。 

// 第四步：编写“全部清除”按钮
// 调用 clearStorage函数 将所有保存在 localStorage 中的数据全部清除。 
```
