<!--
 * @Author: joker.zhang
 * @Date: 2020-08-17 10:20:41
 * @LastEditors: joker.zhang
 * @LastEditTime: 2020-08-20 18:23:13
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

查看版本
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
# npm命令
## cnpm
淘宝团队做的国内镜像，因为npm的服务器位于国外可能会影响安装。淘宝镜像与官方同步频率目前为 10分钟 一次以保证尽量与官方服务同步
```
npm install cnpm -g --registry=https://registry.npm.taobao.org
```
查看版本
```
$ cnpm -v
cnpm@6.1.1 (D:\mysoftware\nodejs\node_global\node_modules\cnpm\lib\parse_argv.js)
npm@6.14.7 (D:\mysoftware\nodejs\node_global\node_modules\cnpm\node_modules\npm\lib\npm.js)
node@10.16.3 (D:\mysoftware\nodejs\node.exe)
npminstall@3.27.0 (D:\mysoftware\nodejs\node_global\node_modules\cnpm\node_modules\npminstall\lib\index.js)
prefix=D:\mysoftware\nodejs\node_global
win32 x64 10.0.17763
registry=https://r.npm.taobao.org
```
## 安装卸载命令
[参考简书](https://www.jianshu.com/p/fca8274bd8cc)

根据你所在项目文件夹package.json里面的依赖安装
```
npm install
```

安装最新版本
```
npm install @[packagename]
```

全局安装
```
npm install [packagename] -g
```

安装好后写入package.json的dependencies中（生产环境依赖）
```
npm install [packagename] --save
```

安装好后写入package.json的devDepencies中（开发环境依赖）
```
npm install [packagename] --save-dev
```
```
package.json文件中的dependencies字段指定了项目运行所依赖的模块，package.json文件中的devDependencies指定项目开发所需要的模块,项目能不能启动，就看包中是否有依赖
```

查看全局安装包的版本
```
$ npm ls vue-router -g
D:\mysoftware\nodejs\node_global
`-- vue-router@3.4.3
```

查看项目安装的版本
```
$ npm ls vue-router
frontend@1.0.0 C:\Users\17TRACK\eclipse-workspace\joker_tp\testPlatform\frontend
`-- vue-router@3.4.3
```


