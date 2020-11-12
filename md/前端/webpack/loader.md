<!--
 * @Author: your name
 * @Date: 2020-10-06 16:33:38
 * @LastEditTime: 2020-10-06 19:14:20
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\前端\webpack\loader.md
-->
loader|作用
:-:|:-:
style-loader|创建style标签，将JS中的样式资源插入进行，添加到head中生效
css-loader|将css文件编程commonjs模块加载js中，里面的内容是样式字符串
less-loader|将less文件编译成css文件
less|less-loader依赖
url-loader|打包图片(options: {limit:8 * 1024})
file-loader(仅安装)|url-loader依赖
html-loader|处理html中的img图片


plugins|作用
:-:|:-:
html-webpack-plugin|默认创建空的HTML，自动引入打包输出的所有资源(JS/CSS);传入一个对象，复制template属性值的位置的html文件并自动引入打包输出的所有资源(JS/CSS)