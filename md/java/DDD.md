> https://www.bilibili.com/video/BV11q4y1q74f/


DP(Domain Primitive)的三条原则:
1. 让隐性的概念显性化
2. 让隐性的上下文显性化
3. 封装多对象行为

概念归纳:
- DP: 抽象并封装自检和一些隐形属性的计算逻辑，且这些属性是无状态的
- Entity: 抽象并封装单对象有状态逻辑
- Domain Service: 抽象并封装多对象的有状态逻辑
- Repository: 抽象并封装外部数据访问逻辑

流程:
1. 首先对需要处理的业务问题进行总览
2. 然后领域对象(Entity)进行划分，明确每个领域对象的包含的信息和职责边界。并进行跨对象，多对象的逻辑组织(Domain Service)
3. 接着在上层应用中根据业务描述去编排Entity和Domain Service
4. 最后再做一些下水道工作，去对下层的数据访问，RPC调用去做一些具体实现