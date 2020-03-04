# 地理位置定位
## 地理位置定位的作用
* 商业

根据用户位置，提供附近店铺的打折信息
* 社交

显示附近的其他用户；将个人位置信息共享给其他好友
* 地图

定位到用户所在位置，直接显示用户附近地图
* 工具

记录个人足迹
## HTML5 获取当前地理位置
### Geolocation API 概览
* 浏览器提供 geolocation 对象，此对象为 navigator 对象的一个属性
* Geolocation 能获得的具体数据（根据设备情况而定）

latitude 纬度（十进制），例如：38.0441

longitude 经度（十进制），例如：114.51

accuracy 精确度，以米为单位

altitude 海拔，海平面以上以米计

heading 行驶方向，从正北开始以度计

speed 速度，以米/每秒计

timestamp 获取位置的时间
* 检测浏览器兼容性
```
// 通过判断 geolocation 对象是否存在判断浏览器是否支持
// 如果不支持，则不执行获取位置的代码并给出提示信息
window.onload = function(){
  if(navigator.geolocation){
    // 获取位置信息的代码
  }else{
    document.getElementById("tip").innerHTML = "您的浏览器版本过旧，建议使用最新版本谷歌浏览器"
  }
}
```
* Geolocation API 存在于navigator对象中，包含 3 个方法
```
//获取当前地理位置
getCurrentPosition(onSuccess, onError, options) 
//参数1：获取数据成功后执行的回调函数，使用 Position 对象作为唯一的参数
//参数2（可选）：获取数据失败时执行的回调函数，使用 PositionError 对象作为唯一的参数
//参数3 （可选）：可选参数列表，可通过该对象参数设定最长可接受的定位返回时间、等待请求的时间和是否获取高精度定位

function success(position){
  var coords = position.coords;
 // coords.latitude	十进制数的纬度
 // coords.longitude	十进制数的经度
 // coords.accuracy	位置精度
 // coords.altitude	海拔，海平面以上以米计
 // coords.altitudeAccuracy	位置的海拔精度
 // coords.heading	方向，从正北开始以度计
 // coords.speed	速度，以米/每秒计
 // timestamp	响应的日期/时间
  console.log('纬度' + coords.latitude);
  console.log('经度' + coords.longitude);
};
function error(err){
  console.log(err.code + ':' + err.message);
};
var options={
 timeout:5000
};
navigator.geolocation.getCurrentPosition(success,error,options);

// 为什么使用回调函数的方式处理数据获取？
// 获取数据的时间可能很长，使用回调函数的方式可以避免程序一直处于等待状态
```
```
watchPosition(onSuccess, onError, options)      //持续监视当前地理位置
// 参数同 getCurrentPosition 相同
// 监测用户位置，位置发生改变时即调用成功回调函数
// 清除监控：该方法会返回一个 ID，如要取消监听可以通过
```
```
clearWatch(watchId)         //清除监视
// 传入该 ID 实现取消的目的
```
