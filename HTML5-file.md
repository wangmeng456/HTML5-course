# 文件
## file对象与filelist对象
* FileList对象与file对象
  
  file对象指用户选择的文件；FileList对象指用户选择的文件列表。
* file对象
  name：文件名，该属性只读。
  
  size：文件大小，单位为字节，该属性只读。
  
  type：文件的 MIME 类型，如果分辨不出类型，则为空字符串，只读。
  
  lastModified：文件的上次修改时间，格式为时间戳。
  
  lastModifiedDate：文件的上次修改时间，格式为 Date 对象实例。
* FileList对象

  ```
   <input type="file" id="file" multiple size="80"/>
  ```
## Blob对象

  file 对象继承了 Blob 对象
  
  Blob 对象表示二进制原始数据。
  
* slice()       可以访问到字节内部的原始数据块。
* size属性    表示一个Blob对象的字节长度。 
* type属性   表示Blob的MIME类型，如果是未知类型，则返回一个空字符串。
  
  image/* 表示图片文件
  
  audio/* 表示音频文件 HTML5
  
  video/* 表示视频文件 HTML5
## FileReader对象

  FileReader 对象用来把文件读入内存，并且读取文件中的数据。
* 检查浏览器对FileReader 对象的支持
  ```
  // if ( typeof FileReader == 'undefined' ) 
  if ( ! window.FileReader ){
    alert( " 您的浏览器未实现 FileReader 接口 " ); 
	}else {                  
		var reader = new FileReader();   
	} 
  ```
* FileReader 对象的方法
  
  无论读取成功或失败，不返回结果，只存储在FileReader的result属性中。
  
  abort	none	中断读取
  
  readAsBinaryString	file	将文件读取为二进制字符串。通常将它传送到服务器端以存储文件。
  
  readAsDataURL	file	将文件读取为 DataURL。读取内容可以做为URL属性，即可以将一个图片的结果指向给一个img的src属性。
  
  readAsText	file, [encoding]	将文件读取为文本数据。第一个参数传入Blog对象，第二个参数传入编码格式。
* FileReader对象的事件

  onabort	数据读取中断时触发
  
  onerror	数据读取出错时触发
  
  onloadstart	读取开始时触发
  
  onprogress	读取中
  
  onload	文件读取成功完成时触发
  
  onloadend	读取完成触发，无论成功或失败
* readAsDataURL()
  
  读取Blob 或 File 对象，完成时触发 loadend 事件，result 属性包含一个data:URL格式的字符串（base64编码）表示所读取文件的内容。
  ```
  var reader  = new FileReader()
  reader.readAsDataURL(file)
  reader.result
  ``` 
