<!--
 * @Author: your name
 * @Date: 2020-03-31 19:16:56
 * @LastEditTime: 2020-03-31 19:21:08
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings E
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\java\Junit断言.md
 -->
Assert.方法
例
Assert.assertEquals(期望的值,程序的变量);

@After和@Before
@Before 一般使用在初始化方法init(){
    //资源的申请所有测试方法先执行前先执行此方法
}
@After 一般在关闭方法close(){
    //在所有的方法执行完，都会执行此方法
}