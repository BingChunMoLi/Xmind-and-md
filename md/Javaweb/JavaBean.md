  JavaBean
  方法声明|功能描述
  :-:|:-:
  static void populate(Object bean,Map<String,?extends Object> properties)|根据指定名称/值对应相应的JavaBean属性设置值
  static void setProperty(Object bean,String name,Object value)|设置指定的属性值，传入的类型要求能转换成相应属性的类型
  static String get Property(Object bean,String name)|返回指定bean指定属性的值，返回类型为String类型
  