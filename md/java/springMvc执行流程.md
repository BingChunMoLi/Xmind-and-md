1. 所有请求经过前端控制器(DispatcherServlet)调用doDispatch方法进行处理
2. 根据HandlerMapping中保存的请求映射信息找到,处理当前请求的处理器执行链(包含拦截器)
3. 根据处理器找到他的适配器(HandlerAdapter)
4. 拦截器的preHandle先执行
5. 适配器执行目标方法
    1. ModelAttribute注解标注的方法提前运行
    2. 执行目标方法时候(确定目标方法用的参数)
        1. 有注解
        2. 无注解
            1. 是否Model、Map以及其他
            2. 是否是自定义类型
                1. 从隐含模型中查看是否存在,存在即get
                2. 如果没有,再看SessionAttributes标注的属性,如果从session中拿，拿不到抛异常
                3. 都不是,利用反射创建对象
6. 拦截器的postHandler执行
7. 处理结果: 渲染页面
    1. 如果有异常使用异常解析器处理异常;处理完成返回ModelAndView
    2. 调用render进行页面渲染
        1. 视图解析器根据视图名得到视图对象
        2. 视图对象调用render方法
        3. 执行拦截器的afterCompletion方法



![](https://cdn.jsdelivr.net/gh/LeagueJinx/img/20210505232639.png)        