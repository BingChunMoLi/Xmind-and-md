检查当前settings
```shell
mvn help:effective-settings
```

maven捆绑方式地址
```path
C:\Users\你的用户\AppData\Local\JetBrains\Toolbox\apps\IDEA-U\ch-0\数字文件名\plugins\maven\lib\maven3\conf
```

maven失败文件：
```file_suffix
.lastUpdated
```

一级子模块打包:
```shell
mvn -B clean package -Dmaven.test.skip=true -Dautoconfig.skip -pl artifactId -am
```
一级子模块的子模块打包:
```shell
mvn -B clean package -Dmaven.test.skip=true -Dautoconfig.skip -pl groupId:artifactId -am
```
> 注: 子模块的子模块groupId不可省略

-pl 指定子模块
-am 根据所需依赖模块，关联打包