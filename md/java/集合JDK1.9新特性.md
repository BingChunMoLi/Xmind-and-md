<!--
 * @Author: your name
 * @Date: 2020-03-25 19:05:39
 * @LastEditTime: 2020-03-25 19:10:09
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\java\集合JDK1.9新特性.md
 -->
List,Set,Map接口增加静态方法of,可以给集合一次性添加多个元素
statix <E> list<E> of (E... elements)
使用前提:当集合中存储的元素个数已经确定了,不在改变时使用
注意:of方法只是用过List接口,Set接口,Map接口,不适用与该接口的实现类
of方法的返回值是一个不能改变的集合,集合不能再使用add,put方法添加元素,会抛出异常
Set接口和Map接口再调用of方法的时候不能有重复的元素,否则会抛出异常