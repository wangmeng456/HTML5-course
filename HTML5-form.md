# 表单
## 新增 input 输入类型
* 数值输入文本框
```
// 注：外观与text文本框相同，但不能输入数值以外的文字，否则提交时将内容作为空白进行提交。
<input  type="number"  name="demoNum"  min="1" max="100" step="2"/>
```
* 邮箱输入文本框
```
// 注：专门用来输入email地址。当表单提交时，会自动校验是否符合邮箱的正则表达式，但不检验该email地址是否存在。  
<input  type="email"  name="email" placeholder="请输入邮箱"  />
```
* url 输入文本框
```
// 专门用来输入url地址。当表单在提交前，会自动校验是否符合url网址的规范。
<input  type="url"  placeholder= "输入正确的网址" />
```
* 电话号码输入文本框
```
<input type="tel"  placeholder="输入电话" name="p"/>
```
* 滑动条输入文本框
```
// 用于应该包含一定范围内数字值的输入域。range 类型显示为滑动条。能够设定对所接受的数字的限定。
<input type="range" min="0" max="50" step="5" name="rdemo" value="0" />
```
* 日期时间输入文本框
```
<input type="date" name="datedemo" />
```
* 颜色选择文本框
```
<input type="color"  name="col"/>
```
* 搜索功能文本框
```
<input type= " search"  name="movie"/>

```
## 新增表单元素
* datalist 元素——为输入框提供可选的列表
```
金庸武侠小说中的武功及招式: <input type="search" name="gongfu"  autocomplete="on" list="names" />
<datalist id="names">
	<option>亢龙有悔</option>
	<option>飞龙在天</option>
	<option>神龙摆尾</option>
	<option>弹指神通</option>
</datalist>
```
* output 元素用于在浏览器中显示计算结果或脚本输出
```
<output  name="x"  for="a b"></output>
```
## 新增表单属性
* form 属性规定输入域所属的一个或多个表单，属性值为所属表单的 id
```
<form  id="testform"  method="get"  action="form.asp">
	姓名:<input type="text" name="name1">
		   <input type="submit" value="提交"/>
</form>
自我介绍：<textarea name="area1" form="testform"></textarea>
```
* required 属性

布尔属性

规定输入域在提交之间必须填写
* placeholder 属性

没有值时出现在文本框中的字符串

获取焦点输入时框中提示信息消失

以柔和的灰色文本方式显示在域中
* list 属性

input 元素的 list 属性与 datalist 元素的 id 属性绑定

提供列表输入选项(如上金庸武侠小说实例代码)
* autofocus 属性

布尔属性，页面加载时表单域自动聚焦

一个页面此属性仅可设置一次
* multiple 属性

用于文件上传控件，设置此属性后，允许上传多个文件
* max/min/step 属性

设置最大值/ 最小值/ 数值或日期时间的增量
