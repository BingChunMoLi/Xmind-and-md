# 最终总结   
正确配置分为两种情况
- ## open Create Java EE 6 annotated class 
> 关闭XML生成，启用 Create Java EE 6 annotated class，  
> 使用servlet 3.0 注解部署项目。
> 需注意 默认生成 @WebServlet(name = "Servlet")  
> 需增加 urlPatterns = "/路径名"  
> 实际为 @WebServlet(name = "Servlet"，urlPatterns = "/servlet" )
- ## off Creat Java EE 6 annotated class
>启用XML自动生成，servlet创建时取消勾选Create Java EE 6 annotated class,  
>使用web.xml部署项目（自动添加）  
>使用servlet--mapping,servlet-name,servlet-class
