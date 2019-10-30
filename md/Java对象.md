<!--
 * @Descripttion: 
 * @version: 
 * @Author: bingyantang
 * @Date: 2019-10-25 08:22:02
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-10-25 15:06:46
 -->
1. 形式参数和返回值的问题:

    (1)形式参数:
     - 类名:需要该类的对象
     - 抽象类名:需要该类的子类对象
     - 接口名:需要该接口的实现类对象
  
    (2)返回值类型:
     - 类名:返回的时该类的对象
     - 抽象类名:返回的是该类的子类对象
     - 接口名:返回的是该接口的实现类对象
    
    (3)链式编程

    对象.方法1().方法2().....方法n();

    这种用法:
    - 其实在方法1()调用完毕后应该返回一个对象
    - 方法2()调用完毕后应该返回一个对象
    - 方法n()调用完毕后,可能是一个对象,也可以不是对象.
2. 包
   1. 其实就是文件夹
   2. 作用:
      1. 区分同名的类
      2. 对类进行分类管理
         1. 按照功能分
         2. 按照模块分
      3. 包的定义   
            package 包名    
            多级包用.分开
       1. 注意事项: 
            - package语句必须在文件的第一条有效语句
            - 在第一个java文件中,只能有一个package
            - 如果没有package,默认是无包名
  
        5.带包的编译和运行 
        - 自动式(Javac -d . Helloworld.java)
        - 手动式
3. 导包
   1. 多次使用带包的类比较麻烦,这个时候java提供了一个关键字import.
   2. 格式:
        import 包名...类名; 
        另一种: 
        import包名...*;
   3. package,import,class的顺序    
   package > import > class
4. 权限修饰符
   1. 权限修饰符
   
    || 本类 | 同一个包名下 | 不同包下的子类 | 不同包下的子类 | 
    |:-:|:-:|:-:|:-:|:-:| 
    | private|Y|N|N|N| 
    | 默认 |Y|Y|N|N| 
    |protected|Y|Y|Y|N| 
    |public|Y|Y|Y|Y| 
    1. 这四种权限修饰符在任意时刻只能出现一种   
   public class Demo{}   
5. 常见的修饰符
   1. 分类:  
   权限修饰符:private,默认,protected,public  
   状态修饰符:static,final  
   抽象修饰符:abstract
   2. 常见的类及其组成的修饰  
   - 类:  
   默认,public,final,abstract
   常用的:public  
   - 成员变量:  
   private,默认,protected,public,static,final
   - 常用的:private  
   - 构造方法:  
    private,默认,protected,public  
    常用:bublic  
    - 成员方法:  
    private,默认,protected,public,static,final,abstract  
    常用:public

    权限|默认|private|protected|public|static|final|abstract
    :-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:
    类|默认|||**1**||1|1
    成员变量|默认|**1**|1|1|1|1|
    构造方法|默认|1|1|**1**||||
    成员方法|默认|1|1|**1**|1|1|1|
    3. 另外比较常见的:  
    public static final int x = 10;  
    public static void show(){}  
    public final void show(){}  
    public abstract void show(){}
6. 内部类:
    1. 把类定义在另一个类的内部，该类就被称为内部类。  
        举例：把类B定义在类A中，类B就被称为内部类。
    2. 内部类的访问规则：  
        1. 可以直接访问外部类的成员，包括私有。
        2. 外部类想要访问内部类的成员，必须创建对象。
    3. 内部类的分类：
       1. 成员内部类
       2. 局部内部类
    4. 成员内部类：
       1. private 为了数据的安全性
       2. static 为了访问的方便性（存疑）
    
       3. 成员内部类不是静态的：  
            外部类名.内部类名 对象名 = new 外部类名.new 内部类名();
       4. 成员内部类是静态的:  
            外部类名.内部类名 对象名 = new 外部类名.内部类名();
    5. 成员内部类的面试题(看程序写结果)
    ```Java
    30,20,10
    
    class Oter{
        public int num = 10;
        class Inner{
            public int num = 20;
            public void show(){
                int num = 30;
                System.out.println(S1);
                System.out.println(S2);
                System.out.println(S3);
            }
        }
    }

填入S1,S2,S3得到输出结果（30，20，10）  
S1 = num  
S2 = this.name  
S3 = super.name or new Outer().num or Outer.this.num  
   6. 局部内部类：  
      1. 局部内部类访问局部变量必须加final修饰。  
      2. 为什么呢？  
        因为局部变量使用完毕就消失，而堆内存的数据并不会立即消失。  
        所以，堆内存还是用该变量，而该变量已经没有了。    
        该值还存在，就加final修饰。  
        通过反编译工具可以看到，加入final后，堆内存存储的是值，而不是变量名。  
    7. 匿名内部类  
        1. 是局部内部类的简化形式  
        2. 前提: 存在一个类或者接口  
        3. 格式:   
            new 类名或者接口名（）{
                重写方法；
            }  
        4. 本质： 其实是继承该类或者实现接口的子类匿名对象  
    8. 匿名内部类在开发中的使用：  
        我们在开发中，会看到抽象类，或者接口参数，而这个时候，我们知道实际的是一个子类对象。  
        如果该方法仅仅调用一次，我们就可以使用匿名内部类的格式简化。
    ```Java
    
    Interface Person{
        public abstract void study();
    }
    Class PersonDemo {
        public void method (Person p){
            p.study();
        }
    }
    Class PersonTest{
        public static void main (String[] args){
            PersonDemo pd = new PersonDemo();
            pd.methon(new Person()){
                public void study(){
                    System.out.println("好好学习,天天向上");
                }
            }
        }
    }

9. 匿名内部类的面试题:  
    ```Java
    Interface Inter{
        void show();
    }
    Class Outer {
        //补齐代码
        //public static Inter method(){
        //    return new Inter(){
        //        public void show (){
        //           System.out.println("HelloWorld");
        //        }
        //    }
        //}
    }
    Class OuterDemo{
        public static void main (String[] args){
            Outer.method().show();  //"HelloWorld"
        }
    }
