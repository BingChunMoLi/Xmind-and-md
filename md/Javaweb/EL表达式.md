## EL表达式：
```
${表达式}
```
### EL标识符
- 不能以数字开头
- 不饿能是EL中的保留字，如and、or、gt
- 不能是EL隐式对象，如pageContext
- 不能包含单引号(`)、双引号(")、减号(-)和正斜杠(/)等特殊字符
### EL中的保留字
and     eq      gt      true        instanceof
or      ne      le      false       empty
not     it      ge      null        div     mod
### EL中的变量
$(product)
### EL中的常量
1. 布尔常量:  
    true and false
2. 整型常量:  
    Long.MIN_VALUE-Long.MAX_VALUE<font color=BlanchedAlmond>$(-2)^{63}$~$2^{63}-1$</font>
3. 浮点数常量:  
    Double.MIX_VALUE-Double.MAX_VALUE()<font color=BlanchedAlmond>$4.9E-324$~$1.8E308$</font>
4. 字符串常量:  
    字符串本身的单引号和双引号需要使用反斜杠转义，如果字符串中含有反斜杠则需要双反斜杠转义
5. Null常量:  
    变量引用对象为空
### EL中的运算符
1. 点运算符:  
   访问某些对象的属性
2. 方括号运算符:  
   与点运算符相同，但当获取的属性名包含一些特殊符号，如"-"、"?"等非字母或数字符号，就只能通过方括号运算符来访问该属性
3. 算术运算符:  
   进行算数运算：特殊 "/"or"div"、"%"or"mod"等价
4. 比较运算符:  
   比较操作书的大小：特殊 "=="or"eq"、"!="or"ne"、"<""it"、">"or"gt"、"<="or"le"、">="or"ge"
   - 注为了避免JSP页面的标签产生冲突，对于大于、小于、大于等于、小于等于四种运算符，如果运算符是主子，且使用关键字代替，那么在运算符和数字直接至少要有一个空格，但后面如果有其他符号可以不加空格。
5. 逻辑运算符:  
   "&&"or"and"、"||"or"or"、"!or"not"、""or""
6. empty运算符:  
   用于判断某个对象是否为null或" ",结果为布尔类型
   ```
   基本语法格式：${empty var}
   ```
7. 条件运算符:  
   ${a?b:c}
8. 圆括号运算符:  
   更改运算符的优先级
   优先级|运算符
   :-:|:-:
   1|[]
   2|()
   3|-(unary) not ! empty
   4|* / div % mod
   5|+ -(binary)
   6|< > <= >= it gt le ge
   7|== != eq ne
   8|&& and
   9| \|\| or
   10|?=
- 注：在应用EL表达式取值时，没有数组的下标越界，没有空指针异常，没有字符串拼接。
## EL隐式对象
隐式对象名称|描述
:-:|:-:
pageContext|对应于JSP页面中的pageContext对象
pageScope|代表page域中用于保存属性的Map对象
requestScope|代表request域中用于保存属性的Map对象
sessionScope|代表session域中用于保存属性的Map对象
applicationScope|代表application域中用于保存属性的Map对象
param|表示一个保存了所有请求参数的Map对象
paramValue|表示一个保存了所有请求参数的Map对象，它对于某个请求参数，返回的是一个String类型数组
header|表示一个保存了所有HTTP请求都字段的Map对象
headerValue|表示一个保存了所有HTTP请求字段的Map对象，返回String类型数组
cookie|用来取得使用者cookie值，cookie类型是Map
initParam|表示一个保存了所有Web应用初始化参数的Map对象
### pageContext对象
```
${pageContext.response.characterEncoding}
```
### Web域相关对象
```
${pageScope.userName}
${requestScope.userName}
${sessionScope.userName}
${applicationScope.userName}
```
### param和paramValues对象
```
${param.nnum}
${paramValues.nums[0]}
```
- 注:param对象获取请求参数的某个值，它是Map类型，与request.getParameter()方法相同，在使用EL获取参数时，如果参数不存在返回空字符串
### Cookie对象
```
获取Cookie对象的信息:${cookie.userName}
获取Cookie对象的名称:${cookie.userName.name}
获取Cookie对现象的值:${cookie.userName.value}
```