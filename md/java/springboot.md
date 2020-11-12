<!--
 * @Author: your name
 * @Date: 2020-05-14 17:12:36
 * @LastEditTime: 2020-11-03 09:31:27
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\java\springboot.md
 -->
@ConfigurationProperties(prefix="配置文件中的ID") //告诉springboot将本类的所有属性和配置文件中的配置进行绑定
prefix="" 告诉springboot 配置文件中的哪一个下面的所有属性与本类相绑定



6.1. 一些常用的字段验证的注解
@NotEmpty 被注释的字符串的不能为 null 也不能为空
@NotBlank 被注释的字符串非 null，并且必须包含一个非空白字符
@Null 被注释的元素必须为 null
@NotNull 被注释的元素必须不为 null
@AssertTrue 被注释的元素必须为 true
@AssertFalse 被注释的元素必须为 false
@Pattern(regex=,flag=)被注释的元素必须符合指定的正则表达式
@Email 被注释的元素必须是 Email 格式。
@Min(value)被注释的元素必须是一个数字，其值必须大于等于指定的最小值
@Max(value)被注释的元素必须是一个数字，其值必须小于等于指定的最大值
@DecimalMin(value)被注释的元素必须是一个数字，其值必须大于等于指定的最小值
@DecimalMax(value) 被注释的元素必须是一个数字，其值必须小于等于指定的最大值
@Size(max=, min=)被注释的元素的大小必须在指定的范围内
@Digits (integer, fraction)被注释的元素必须是一个数字，其值必须在可接受的范围内
@Past被注释的元素必须是一个过去的日期
@Future 被注释的元素必须是一个将来的日期

我们在需要验证的参数上加上了@Valid注解，如果验证失败，它将抛出MethodArgumentNotValidException。
```java
@RestController
@RequestMapping("/api")
public class PersonController {

    @PostMapping("/person")
    public ResponseEntity<Person> getPerson(@RequestBody @Valid Person person) {
        return ResponseEntity.ok().body(person);
    }
}
```
6.3. 验证请求参数(Path Variables 和 Request Parameters)
一定一定不要忘记在类上加上 Validated 注解了，这个参数可以告诉 Spring 去校验方法参数。

@RestController
@RequestMapping("/api")
@Validated
public class PersonController {
```java
    @GetMapping("/person/{id}")
    public ResponseEntity<Integer> getPersonByID(@Valid @PathVariable("id") @Max(value = 5,message = "超过 id 的范围了") Integer id) {
        return ResponseEntity.ok().body(id);
    }
}
```
7. 全局处理 Controller 层异常
介绍一下我们 Spring 项目必备的全局处理 Controller 层异常。

相关注解：

@ControllerAdvice :注解定义全局异常处理类
@ExceptionHandler :注解声明异常处理方法
如何使用呢？拿我们在第 5 节参数校验这块来举例子。如果方法参数不对的话就会抛出MethodArgumentNotValidException，我们来处理这个异常。
```java
@ControllerAdvice
@ResponseBody
public class GlobalExceptionHandler {

    /**
     * 请求参数异常处理
     */
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<?> handleMethodArgumentNotValidException(MethodArgumentNotValidException ex, HttpServletRequest request) {
       ......
    }
}
```