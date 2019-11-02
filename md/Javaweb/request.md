```java        
        String q = request.getMethod();
        out.print("请求方式:" + q +"<br>");
//        获取HTTP请求消息中的请求方式（如GET、POST等）
        String z = request.getRequestURI();
        out.print("资源名称：" + z +"<br>");
//        用于获取请求行中的资源名称部分，即位于URL的主机和端口之后、参数部分之前的部分
        String c = request.getQueryString();
        out.print("参数:" + c +"<br>");
//        用于获取请求行中的参数部分，也就是资源路径后面问号（？）以后所有的内容
        String h = request.getProtocol();
        out.print("协议名与版本:" + h +"<br>");
//        用于获取请求行中的协议名和版本，例如HTTP/1.0或HTTP/1.1
        String path = request.getContextPath();
        out.print("Web应用程序的路径:" + path +"<br>");
//        该方法用于获取请求URl中属于Web应用程序的路径，这个路径由“/”开头，表示相对于整个Web站点的根目录，路径结尾不含“/”。如果请求URl属于Web站点的根目录，那么返回结果为空字符串（“”）
        String Servlet_Name = request.getServletPath();
        out.print("Servlet名称与映射路径:" + Servlet_Name +"<br>");
//        用于获取Servlet的名称或Servlet所映射的路径
        String S_Name = request.getRemoteHost();
        out.print("获取请求客户端的完整主机名:" + S_Name +"<br>");
//        该方法用于获取请求客户端的完整主机名，其格式类似于"pc1.leaguejinx.xyz"，需要注意的是，如果无法解析出客户机的完整主机名，该方法将会返回客户端的IP地址
        String IP = request.getRemoteAddr();
        out.print("请求客户端的Ip:" + IP +"<br>");
//        用于获取请求客户端的IP地址，其格式类似于“192.168.*.*”
        int port = request.getRemotePort();
        out.print("请求客户端的端口号:" + port +"<br>");
//        该方法用于获取请求客户端网络连接的端口号
        String IP2 = request.getLocalAddr();
        out.print("Web服务器接收请求的IP地址:" + IP2 +"<br>");
//        用于获取Web服务器上接受当前请求网络连接的IP地址
        String Sname = request.getLocalName();
        out.print("Web服务器接受请求的主机名:" + Sname +"<br>");
//        该方法用于获取Web服务器上接受当前网络连接IP所对应的主机名
        int port2 = request.getLocalPort();
        out.print("Web服务器上接受当前网络连接的端口号:" + port2 +"<br>");
//        用于获取Web服务器上接受当前网络连接的端口号
        String name3 = request.getServerName();
        out.print("请求指向的主机名（HTTP消息中Host头字段）:" + name3 +"<br>");
//        用于获取当前请求所指向的主机名，即HTTP请求消息中Host头字段所对应的主机名部分
        int portq = request.getServerPort();
        out.print("请求链接所链接服务器的端口号(HTTP请求消息中Host头字段对应的端口号部分):" + portq +"<br>");
//        用于获取当前请求连接所连接服务器端口号，即如果Http请求消息中Host头字段所对应的端口号部分
        String http = request.getScheme();
        out.print("请求协议名:" + http +"<br>");
//        用于获取请求的协议名,例如http,https,ftp
        StringBuffer URl = request.getRequestURL();
        out.print("完整URL:" + URl +"<br>");
//        用于获取客户端发送请求时的完整URL，包括协议、服务器名、端口号、资源路径等信息，但不包括后面查询参数部分。注意，getRequestURL()方法返回的结果是StringBuffer类型不是String类型，这样便于对于结果的修改
```