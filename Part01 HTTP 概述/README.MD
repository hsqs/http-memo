# Part01 HTTP 概述

### 1.1 HTTP--因特网的多媒体信使
&emsp;&emsp;HTTP使用的是可靠的数据传输协议，因此即使是数据来自地球的另一端，它也能确保数据再传输过程中不会被损坏或产生混乱。

### 1.2 Web客户端和服务器
&emsp;&emsp;浏览一个页面时，浏览器会向服务器发送一条HTTP请求，如果成功，服务器会将对象、对象类型、对象长度等其他信息放在HTTP响应中发送给客户端。

### 1.3 资源
&emsp;&emsp;1、最简单的Web资源就是Web服务器上的静态文件，可以是文本、HTML文件、office文件、图片、视频文件等。  
&emsp;&emsp;2、相对的，也存在动态资源，根据用户身份信息、用户偏好、时间段等来动态生成。

##### 1.3.1 媒体类型
&emsp;&emsp;1、因特网上有数千种不同的数据类型，HTTP仔细的给每种要通过Web传输的对象都打上了MIME类型的数据格式标签。  
&emsp;&emsp;2、Web浏览器从服务器取得一个对象时，会查看相关的MIME类型，看看自己是否有能力处理这个对象。  
&emsp;&emsp;3、MIME类型是一种文本标记，表示一种主要的对象类型和一个特定的子类型，中间用‘/’隔开，例如 text/html、image/gif。

##### 1.3.2 URI
&emsp;&emsp;URI(Uniform Resource Identifier)，统一资源标识符。有URL和URN两种形式。

##### 1.3.3 URL
&emsp;&emsp;URL，统一资源定位符。大部分URL都包含三个部分：  

|    部位     | 描述           | 
| ------------- |:-------------| 
| schema      | 说明访问资源用到的协议，一般指HTTP协议（http://） | 
| 服务器地址| 再因特网上的地址，域名或者IP地址等，例如：www.ruokay.com |
| 资源路径| 指定了资源在Web服务器上的位置， 例如 /1/2/3.html |

&emsp;&emsp;现在，几乎所有的URI都是URL。

##### 1.3.4 URN
&emsp;&emsp;URN，同意资源名，作为特定内容唯一名称使用，与目前的资源所在位置无关。例如：urn:ierf:rfc:2141。目前仍处于试验阶段。

### 1.4 事务
&emsp;&emsp;一个HTTP事务是由一条请求命令和一个响应结果组成。请求和响应通过HTTP报文（HTTP message）来传输。

##### 1.4.1 方法（HTTP method）
&emsp;&emsp;常见的HTTP方法：   

|    HTTP 方法     | 描述           | 
| ------------- |:-------------| 
| GET | 从服务器向客户端发送命名资源 | 
| PUT | 讲来自客户端的数据存储到一个命名的服务器资源中 |
| DELETE | 从服务器删除命名资源 |
| POST | 讲客户端数据发送到一个服务器网关应用程序 |
| HEAD | 仅发送命名资源响应中的HTTP首部 |

##### 1.4.2 状态码
&emsp;&emsp;1、每条HTTP响应报文返回时，都会携带一个状态码。状态码是一个三位的数字，告知客户端请求是否成功或需要采取其他动作。
&emsp;&emsp;2、伴随状态码，HTTP还会发生一条解释的“原因短语”，例如：200 OK、404 Not Found。
&emsp;&emsp;3、对于相同状态码，可以对应不同描述短语，HTTP程序处理时，只会以状态码为准。

### 1.5 报文
&emsp;&emsp;1、HTTP报文都是纯文本，不是二进制代码，所以人们可以方便的读写。（二进制形式可能对程序来说容易处理，但纯文本形式易于扩展阅读和调试）。
&emsp;&emsp;2、HTTP报文只有两种，请求报文（request message）和响应报文（response message）。二者格式很类似
&emsp;&emsp;3、HTTP报文包含3个部分：

|     部位     |     描述    |
|    ---       |    ---     |
| 起始行 | 报文的第一行，请求报文里说明要做什么，响应报文里说明出现了什么情况 |
| 首部字段 | 起始行后面跟0到多个首部字段，首部字段以键值对形式出现，用冒号（:）隔开，首部字段以一个空行作为结束标志 |
| 主体 | 空行之后是可选的报文主体，与结构化的起始行和首部不同的是，主体可以使任意二进制数据或者文本 |

##### 1.5.1 简单的报文实例
&emsp;&emsp;1、请求报文
```http
GET /tools.html HTTP/1.0
User-agent: Mozilla/4.75 [en]
Host: www.ruokay.com
Accept: text/html, image/gif, image/jpeg
Accept-language: en
```
&emsp;&emsp;2、响应报文
```http
HTTP/1.0 200 OK
Date: Sun, 01 Oct 2001 22:22:22 GMT
Server: Apache/1.3.11 BSafe-SSL/1.38(Unix)
Last-Modified: Tue, 04 Jul 2000 09:46:21 GMT
Content-type: text/html
Content-length: 444

<html>
<head>
<title>ruokay</title>
</head>
</html>
```