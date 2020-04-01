<!--
 * @Author: 冰彦糖
 * @Date: 2020-03-29 11:49:38
 * @LastEditTime: 2020-03-31 19:12:18
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\java\Lambda表达式.md
 -->
使用前提:
1. 使用Lambda必须具有接口、且要求接口**有且仅有一个抽象方法**.
无论使用JDK内置的Runnable、Comparator接口还是自定义接口,只有当接口中抽象方法存在且唯一时才可以使用Lambda
2. 使用Lambda必须有上下文推断.也就是方法的参数或局部变量必须为Lanmbda对应的接口类型,才能使用Lambda作为该接口的实例
PS: 有且仅有一个抽象方法的接口,称为**函数式接口**；

1. (参数列表):括号中参数列表的数据类型,可以省略不写
2. (参数列表):括号中的参数如果只有一个,那么类型和()都可以省略不写
3. (一些代码):如果{}只有一行,无论是否有返回值,都可以省略{},;,return,
PS: 要省略{},;,return 必须一起省略




接口添加@Functionalnterface 检测是否是一个函数式接口