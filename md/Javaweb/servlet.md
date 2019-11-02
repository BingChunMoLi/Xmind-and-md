```java
    /*
    PrintWriter out = response.getWriter();                             //java.io.PrintWriter是java中很常见的一个类，该类可用来创建一个文件并向文本文件写入数据。可以理解为java中的文件输出，java中的文件输入则是java.io.File
    Writer
    用于写入字符流的抽象类。 子类必须实现的唯一方法是write（char []，int，int），flush（）和close（）。 然而，大多数子类将覆盖这里定义的一些方法，以便提供更高的效率，附加的功能或两者。
    构造方法
    Modifier(私有性)	Constructor and Description(构造函数及描述)
    protected	Writer()
    创建一个新的字符流 writer，其关键部分将同步 writer 自身。
    protected	Writer(Object lock)
    创建一个新的字符流写入器，其关键部分将在给定对象上进行同步。（创建一个新的字符流 writer，其关键部分将同步给定的对象。）
    */
    ServletConfig config = this.getServletConfig();                     //获得ServletConfig对象
    /*
    作用：
    1.配置Servlet初始化参数
    2.通过ServletConfig获取Servlet的初始化参数
    */
    String p = config.getInitParameter("encoding");                 //获取encoding名的属性值
    ServletContext c = this.getServletContext();                        //获取ServletContext对象
    /*
    WEB容器在启动时，它会为每个WEB应用程序都创建一个对应的ServletContext对象，它代表当前web应用。
　　ServletConfig对象中维护了ServletContext对象的引用，开发人员在编写servlet时，可以通过ServletConfig.getServletContext方法获得ServletContext对象。
　　由于一个WEB应用中的所有Servlet共享同一个ServletContext对象，因此Servlet对象之间可以通过ServletContext对象来实现通讯。ServletContext对象通常也被称之为context域对象。
    作用：
    1.多个Servlet通过ServletContext对象实现数据共享
    2.获取WEB应用的初始化参数
    3.用servletContext实现请求转发
    4.利用ServletContext对象读取资源文件
    5.在客户端缓存Servlet的输出
    */
    Enumeration<String> paramNames =c.getInitParameterNames();          //遍历所有HTTP请求(课本:遍历所有初始化参数名)
    /*
    getProtocol():获取请求使用的通信协议，如http/1.1等
    getServletPath():获取请求的JSP也面所在的目录。
    getContentLength():获取HTTP请求的长度。
    getMethod():获取表单提交信息的方式，如POST或者GET。
    getHeader(String s):获取请求中头的值。一般来说，S参数可取的头名有accept,referrer、accept-language、content-type、accept-encoding、user-agent、host、cookie等，比如，S取值user-agent将获得用户的浏览器的版本号等信息。
    getHeaderNames():获取头名字的一个枚举。
    getHeaders(String s):获取头的全部值的一个枚举。
    getRemoteAddr():获取客户的IP地址。
    getRemoteHost():获取客户机的名称（如果获取不到，就获取IP地址）。
    getServerName():获取服务器的名称。
    getServePort():获取服务器的端口。
    getPaeameterNames():获取表单提交的信息体部分中name参数值的一个枚举
        */
    String date = (String) c.getAttribute("date");//通过getAttribute方法获取属性值
```
