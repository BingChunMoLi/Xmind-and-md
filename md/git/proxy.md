#### 设置 代理：

使用以下命令为该项目配置代理：

```bash
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

#### 移除全局代理设置：

要删除之前设置的全局 Git 代理，可以使用以下命令：

```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```
