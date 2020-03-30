<!--
 * @Author: 冰彦糖
 * @Date: 2020-03-29 16:00:30
 * @LastEditTime: 2020-03-30 17:27:55
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Ei
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\java\File.md
 -->
File类
系统环境|路径分隔符|文件名称分隔符
:-:|:-:|:-:
Java|File.pathSeparator|File.separator
windows|;|\
linux|:|/
PS:File.pathSeparatorChar和File.separatorChar均会返回Char,而不带Char的属性，返回为字符串

jdk1.7之后
```java
try(定义流对象){
    //try代码
}catch(IOException e){
    System.out.pringln(e);
}
```
可省略finally 关闭流对象，自动关闭
JDK9新特性:
```java
IO a = null;
try(a){

}catch(IOException e){
    System.out.pringln(e);
}
```