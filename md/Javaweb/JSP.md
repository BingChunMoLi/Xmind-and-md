### JSP脚本元素
```jsp
<% java代码(变量、方法、表达式等) %>
```
### JSP声明语句
```jsp
<%! 定时的变量或方法等 %>
```
### JSP表达式
```jsp
<%= expression(表达式) %>
```
### JSP注释
```jsp
<%-- 注释 --%>
```
---
### page指令
```jsp
<%@ page 属性名=“属性值” %>
```
#### page的常用属性:  
##### 页面特性描述
属性名称|取值范围|描述
:-:|:-:|:-:
language|java|指明解释该JSP文件时采用的语言，默认为java
import|任何包名、类名|指定在JSP页面翻译成Servlet源文件中导入的包或类。import是唯一可以声明多次的page指令属性。一个import属性可以引用多个类，中间用英文逗号隔开。
session|ture、false|指明该JSP内是否内置Session对象,如果为true,则说明内置Session对象，可以直接使用，否则没有内置Session对象。默认情况下，session属性值true。需要注意的是JSP引擎自动导入以下四个包:java.lang.*;javax.servlet.*;javax.servlet.jsp.*;javax.servlet.http.*;
isErrorPage|true、false|指定该页面是否为错误处理页面，如果为ture，则该JSP内置有一个Exception对象的exception，可直接使用。默认情况下，isErrorPage的值为false
errorPage|某个JSP页面的相对路径|指定错误页面，如果该JSP程序抛出一个未捕获的异常，则转到errorPage指定的页面。errorPage指定的页面的isErrorPage属性为true，且内置的exception对象为未捕获的异常
conteentType|有效的文档类型|客户端浏览器根据该属性判断文档类型(MIME)
pageEnCoding|当前页面|指定页面编码格式
### include属性、
#### 静态包含文件
```jsp
<%@ include file="被包含文件地址" %>
```

## JSP隐式对象
名称|类型|描述
:-:|:-:|:-:
out|javax.servlet.jsp.Writer|用于页面输出
request|javax.servlet.http.HttpServletRequest|得到用户请求信息
response|javax.servlet.http.HttpServletResponse|服务器向客户端回应的信息
config|javax.servlet.ServletConfig|服务器配置，可以取得初始化参数
session|javax.servlet.http.HttpSession|用来保存用户信息
application|javax.servlet.ServletContext|所有用户共享信息
page|java.long.Object|当前页面转换后的Servlet类的实例
pageContext|javax.servlet.jsp.PageContext|JSP的页面容器
exception|java.long.Throwable|表示JSP页面所发生的异常，在错误页中才起作用。

### pageContext对象
- #### 获取隐式对象的方法：
方法名称|功能描述
:-:|:-:
JspWriter getOut()|获取out隐式对象
Object getPage()|获取page隐式对象
ServletRequest getRequest()|获取request隐式对象
Servletresponse getResponse()|获取response隐式对象
HttpSession getSession()|获取session隐式对象
Exception getException()|获取exception隐式对象
ServletConfig getServletConfig()|获取config隐式对象
ServletContext getServletContext()|获取application隐式对象
- ####  操作属性方法:
方法名称|功能描述
:-:|:-:
void setAttribute(String name,Object value,int scope)|用于设置pageContext对象属性
Object getAttribute(String name,ini scope)|用于获取pageContext对象的属性
void removeAttribute(String name,int scope)|删除指定范围内名称为name的属性
void removeAttribute(String name)|删除所有范围内名称为name的属性
Object findAttribute(String name)|从4个域对象中查找名称为name的属性
注：scope指定的是属性的作用范围，pageContext对象的作用范围有四个值
- pageContext.PAGE_SCOPE:表示页面范围
- pageContext.REQUEST_SCOPE:表示请求范围
- pageContext.SESSION_SCOPE:表示会话范围
- pageContext.APPLICATION_SCOPE:表示Web应用程序范围
