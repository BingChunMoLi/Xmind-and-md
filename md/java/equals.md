Java语言规范要求equals方法具有下面的特性:
1. 自反性: 对于任何非空引用x,x.equals(x) 应该返回true。
2. 对称性: 对于任何引用x和y，当且仅当y.equals(x)返回true，x.equrals(y)也应该返回true。
3. 传递性: 对于任何引用x,y和z，如果x.equals(y)返回true，y.equals(z)返回true，x.equals(z)也应该返回true。
4. 一致性: 如果x和y引用的对象没有变化，反复调用x.equals(y)应该返回同样的结果。
5. 对于任意非空引用x.x.equals(null) 应该返回false

对于getClass检测和instanceof检测的问题:
- 如果子类能够拥有自己的相等的概念,则对称性需求强制采用getClass进行检测。
- 如果由超类决定相等的概念，那么可以使用instanceof进行检测，这样可以在不同子类的对象之间进行相等的比较。

完美equals方法的建议:
1. 显式参数命名为otherObject，稍后将他转换陈另一个叫做other的变量
2. 检测this与otherObject是否引用同一个对象:
```java
if(this == otherObject) return true;
```
这条语句只是一个优化。实际上这是一种经常采用的形式。因为计算这个等式要比一个一个地比较类中的域所付出的代价小得多。
3. 检测other是否为null，如果为null，返回false。这项检测很有必要
4. 比较this与otherObject是否属于同一个类。如果equals的语义在每个子类中有所改变，就用getClass检测:
```java
if(getClass() != otherObject.getClass()) return false;
```
如果所有的子类都有统一的语义，就使用instanceof检测:
```java
if(!otherObject instanceof ClassName) return false;
```
5. 将otherObject转换为相应的类类型变量:
```java
ClassName other = (ClassName)otherObject
```
6. 现在开始要开始对所有需要比较的域进行比较了。使用==比较基本类型域，使用equals比较对象域。如果所有的域都匹配，就返回true;否则返回false。
```java
return field1 == other.field1 && Object.equals(field2,other.field2) && ...;
```
如果在子类中重新定义equals,就要在其中包含调用super.equals(other)。
注: 对于数组类型的域，可以使用静态Arrays.equals方法检测相应的数组元素是否相等