# HTML5 标签及特性
## HTML5 标签特性
```
<!DOCTYPE html>
  <head>
    <meta charset="utf-8">
    <title>HTML5</title>
  </head>
  <body>
    <p>hello world</p>
  </body>
</html>
```
## HTML5 新增的结构性元素
```
<header>//定义头部，通常包含导航和一些引导信息
<nav>//定义导航内容
<article>//定义正文内容
<section>//定义文章中的端
<aside>//定义边栏内容
<footer>//定义页脚
<header>
  <h1>页眉</h1>
  <nav>导航标签<nav>
</header>
<section>
  <article>
    <p>主要内容，文章正文</p>
  </article>
  <aside>其他内容</aside>
</section>
<section>区段</section>
<footer>页脚</footer>
```
## HTML5 新增的功能性元素
* 多媒体
```
//src	指定音/视频文件的URL地址
//controls	是否添加浏览器自带的播放控制条
//loop	是否循环播放音频/视频
//autoplay	指定媒体是否在页面加载后自动播放
//width	指定视频宽度，只有<video>标签具有
//height	指定视频高度，只有<video>标签具有

<video>//播放视频
// <video src="01.ogg" controls="controls">
//   您的浏览器不支持video标签
// </video>
<video controls="controls">
  <source src="01.ogg" type="video/ogg"> //source可以链接不同的音频文件，浏览器将使用第一个可识别的格式
  <source src="01.mp4" type="video/mp4">
</video>

<audio>//播放音频
// <audio src="02.ogg" controls="controls">
//   您的浏览器不支持audio标签
// </audio>
<audio controls="controls">
  <source src="02.ogg" type="audio/ogg">
  <source src="02.mp4" type="audio/mp4">
</audio>

//play()	加载音频、视频
//pause()	暂停处于播放状态的音频、视频
//load()	重新加载音频、视频元素

<embed src="helloworld.swf" /> //<embed>定义嵌入的内容

// <time>定义公历的时间（24 小时制）或日期
<p>我们在每天早上 <time>8:00</time> 开始上课</p>
<p>我在 <time datetime=“2018-10-1”>国庆节</time> 有个约会</p>

// <details> 标签用于描述文档或文档某个部分的细节。与 <summary> 标签配合使用可以为 details 定义标题。标题是可见的，用户点击标题时，会显示出 details。
<details>
   <summary>Copyright 2018.</summary>
   <p>版权归H5方向所有.</p>
</details>

// <mark> 标签定义带有记号的文本
<p> 每天都要记得吃<mark>早饭</mark> </p>

// <progress> 标签标示任务的进度（进程）。
<progress value="25" max="100"> </progress> 
```
