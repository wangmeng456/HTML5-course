# 离线 web 应用
## 离线Web应用的作用
* 离线浏览 - 用户可在应用离线时使用它们 
* 加快速度 - 已缓存资源加载得更快
* 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源
## 创建离线应用
### 离线技术包含的两个部分
* 缓存清单文件：管理要缓存的文件列表
* JavaScript接口：提供用于更新缓存文件的方法以及对缓存文件的操作。
### 创建离线应用程序
* 第一步：创建缓存清单文件（manifest 文件）

  文件扩展名使用 appcache；

  manifest 文件需要在web服务器上配置正确的 MIME 类型为:text/cache-manifest。
* 第二步：在 html 标记中指定使用缓存文件（每个指定了 manifest 的页面在用户对其访问时都会被缓存）
```
<html manifest="cacheData.appcache">
```
### 离线应用的更新
* 构建离线应用后，即使在线状态，用户也会访问缓存文件
* HTML5离线缓存更新：
  
  1. 用户清空浏览器缓存
  
  2. manifest 文件被修改
  
  3. 由程序来更新应用缓存
## 离线控制的 API
* applicationCache
```
// 通过判断window.applicationCache对象是否存在进行浏览器兼容性检测
window.onload = function(){
  if(window.applicationCache){
    //离线操作API
  }else{
    document.getElementById("info").innerHTML = "你的浏览器已经out了";
  }
}
```
* 离线事件监听

  applicationCache.addEventListener()
* 更新缓存方法

  调用当前应用资源下载过程   applicationCache.update()
  
  更新到最新的缓存，不会使之前加载的资源突然被重新加载   applicationCache.swapCache()
