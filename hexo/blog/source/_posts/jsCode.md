title: js字符编码函数区别分析
date: 2016-05-20 18:11:20
description: 
categories:
- node js字符编码函数
tags:
- node js字符编码函数
toc: true
author: leaf
comments:
original:
permalink: 
---

今天leaf用ajax发送请求，服务端返回的其他字段内容都OK，但是处理中文名称的图片服务端返回来格式正确但是字段名称是乱码（英文是OK的哈，但leaf想尝试中文），于是对于解决传值乱码问题yujuan查了资料，把内容总结如下：

#### JavaScript中有三个可以对字符串编码的函数，分别是：

```

转义方法：
	escape();//函数可对字符串进行编码
	encodeURI();//函数可把字符串作为 URI 进行编码。
	encodeURIComponent();//函数可把字符串作为 URI 组件进行编码。

解码函数方法:
	unescape();
	decodeURI();
	decodeURIComponent();

var  t = escape("<哈哈>");
document.write(t); //输出：%3C%u54C8%u54C8%3E
document.write(unescape(t)); //输出:<哈哈>

转义结果：%3C%u54C8%u54C8%3E   解码结果：<哈哈>
```

#### 详解js的3个对文字编码的函数： escape,encodeURI,encodeURIComponent， 对应的解码函数：unescape,decodeURI,decodeURIComponent

# 一、定义和用法

encodeURI() 函数可把字符串作为 URI 进行编码。

语法
encodeURI(URIstring)

|参数    |描述    |
|:----:|:----:|
|URIstring	|必需。一个字符串，含有 URI 或其他要编码的文本。|

返回值
URIstring 的副本，其中的某些字符将被十六进制的转义序列进行替换。

说明
该方法不会对 ASCII 字母和数字进行编码，也不会对这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。
该方法的目的是对 URI 进行完整的编码，因此对以下在 URI 中具有特殊含义的 ASCII 标点符号，encodeURI() 函数是不会进行转义的：;/?:@&=+$,#

提示和注释
提示：如果 URI 组件中含有分隔符，比如 ? 和 #，则应当使用 encodeURIComponent() 方法分别对各组件进行编码。
此方法的解码为decodeURI()

 

 

# 二、定义和用法

escape() 函数可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。

语法
escape(string)

|参数    |描述   |
|:----:|:----:|
|string	|必需。要被转义或编码的字符串。|

返回值
已编码的 string 的副本。其中某些字符被替换成了十六进制的转义序列。

说明
该方法不会对 ASCII 字母和数字进行编码，也不会对下面这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。其他所有的字符都会被转义序列替换。

提示和注释
提示：可以使用 unescape() 对 escape() 编码的字符串进行解码。
注释：ECMAScript v3 反对使用该方法，应用使用 decodeURI() 和 decodeURIComponent() 替代它。

 

# 三、JavaScript encodeURIComponent() 函数

定义和用法
encodeURIComponent() 函数可把字符串作为 URI 组件进行编码。

语法
encodeURIComponent(URIstring)

|参数	|描述   |
|:----:|:----:|
|URIstring	|必需。一个字符串，含有 URI 组件或其他要编码的文本。|

返回值
URIstring 的副本，其中的某些字符将被十六进制的转义序列进行替换。

说明
该方法不会对 ASCII 字母和数字进行编码，也不会对这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。

其他字符（比如 ：;/?:@&=+$,# 这些用于分隔 URI 组件的标点符号），都是由一个或多个十六进制的转义序列替换的。

提示和注释
提示：请注意 encodeURIComponent() 函数 与 encodeURI() 函数的区别之处，前者假定它的参数是 URI 的一部分（比如协议、主机名、路径或查询字符串）。因此 encodeURIComponent() 函数将转义用于分隔 URI 各个部分的标点符号。
此方法解码方式decodeURIComponent