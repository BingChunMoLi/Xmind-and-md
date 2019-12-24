<!--
 * @Author: 冰彦糖
 * @Date: 2019-12-23 16:06:13
 * @LastEditTime : 2019-12-23 16:34:01
 * @LastEditors  : Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\Javaweb\servlet生命周期.md
 -->
## 创建Servlet对象:
init方法:在这个方法初始化一些对象，比如数据库链接对象  
service方法:用来处理客户端请求  
destory方法: servlet对象销毁的时候自动调用  

init方法特点：只会调用一次  
service方法特点：处理实际请求并返回结果  
wev server每次收到请求会启动新的线程去调用service方法；  
service方法自动的检查请求类型get、post、put、delete、head、options、delete  
在不使用service的时候，就需要重写：doGet、doPost方法  
init和destory方法，根据情况进行重写  
拓展知识：web程序是天生多线程，不必再servlet中手动开线程  
http是无状态的  

## MVC：  
mode1:db mode1 和 view mode1  
v: view  
c: controller  
这与三层结构不一样  
开发servlet的步骤：  
1.从httpservlet继承  
extends HttpSerclet  
