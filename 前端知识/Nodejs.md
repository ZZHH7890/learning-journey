<!--
 * @Author: joker.zhang
 * @Date: 2020-08-17 10:20:41
 * @LastEditors: joker.zhang
 * @LastEditTime: 2020-08-17 14:48:38
 * @Description: For Automation
-->
# 下载安装
```
https://nodejs.org/en/
```
```
$ node -v
v10.16.3
```

# 配置
1. nodejs文件夹下，新建文件夹node_global和node_cache
2. 运行配置命令
```
npm config set prefix "D:\nodejs\node_global"
npm config set cache "D:\nodejs\node_cache"
```
3. 配置一个淘宝镜像站，用于提升速度
```
npm config set registry=http://registry.npm.taobao.org
```
4. npm路径已经改变，添加环境变量路径 D:\mysoftware\nodejs\node_modules
```
$ npm -v
6.9.0
```
5. 检查配置信息npm config list
```
17TRACK@17-20180416LUGI MINGW64 ~
$ npm config list
userconfig C:\Users\17TRACK\.npmrc
cache = "D:\\mysoftware\\nodejs\\node_cache"
prefix = "D:\\mysoftware\\nodejs\\node_global"
registry = "http://registry.npm.taobao.org/"
```