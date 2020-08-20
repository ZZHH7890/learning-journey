<!--
 * @Author: joker.zhang
 * @Date: 2020-08-17 10:20:41
 * @LastEditors: joker.zhang
 * @LastEditTime: 2020-08-20 19:26:25
 * @Description: For Automation
-->
# Vue安装配置
## 配置好Nodejs
## 安装cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
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

## 测试是否能获得vue信息cnpm info vue
```
$ cnpm info vue

vue@2.6.11 | MIT | deps: none | versions: 294
Reactive, component-oriented view layer for modern web interfaces.
https://github.com/vuejs/vue#readme

dist
.tarball: https://registry.npm.taobao.org/vue/download/vue-2.6.11.tgz
.shasum: 76594d877d4b12234406e84e35275c6d514125c5

maintainers:
- yyx990803 <yyx990803@gmail.com>

dist-tags:
csp: 1.0.28-csp
latest: 2.6.11
next: 3.0.0-rc.5

published 8 months ago by yyx990803 <yyx990803@gmail.com>

```

## 配置脚手架vue-cli
安装脚手架
```
cnpm install -g @vue/cli
```

```
$ vue -V
@vue/cli 4.5.4

```

创建项目
```
vue create frontend
```

```
$ cd frontend
$ npm run serve
```

启动,  'DONE  Compiled successfully'证明demo可以使用了，浏览器输入url即可：http://localhost:8093/
```
npm run serve
```
## 配置ant-design-vue
[官网](https://www.antdv.com/docs/vue/getting-started-cn/)

安装带参数--save,记得进入项目目录进行安装，才能写进依赖, 这样在main.js中导入才不会保存
```
cnpm install --save ant-design-vue
```
main.js中导入
```
import Button from 'ant-design-vue/lib/button'
import 'ant-design-vue/dist/antd.css'

Vue.component(Button.name, Button)
```

## 配置axios
```
cnpm install --g axios 
```
main.js
```
import axios from 'axios'
Vue.prototype.axios = axios
```
也可以使用vue-axios
```
cnpm install --g axios vue-axios
```
main.js
```
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)
```

## vue-router
```
https://router.vuejs.org/zh/guide/
```

# 常见问题
## Elements in iteration expect to have 'v-bind:key' directives
[解决](https://www.cnblogs.com/h2zZhou/p/9639984.html)
```
<table class="tb">
      <tr>
        <th>编号</th>
        <th>用例名称</th>
        <th>请求地址</th>
        <th>项目</th>
      </tr>
      <tr v-for="testcase in testcases" :key="testcase.id">
        <td>{{testcase.id}}</td>
        <td>{{testcase.name}}</td>
        <td>{{testcase.url}}</td>
        <td>{{testcase.project}}</td>
      </tr>
    </table>
```
## VSCode格式化vue代码变双引号
在项目根目录下新建一个名为.prettierrc的文件
```
{
  "semi": false,
  "singleQuote": true
}
```
## vue项目运行服务报错

问题
```
npm run dev
npm ERR! missing script: dev

npm ERR! A complete log of this run can be found in:
npm ERR!     E:\nodejs\node_cache\_logs\2018-12-12T15_06_08_674Z-debug.lo
```
解决:检查package.json中的脚本,会发现已经vue-cli3.0脚手架没有了dev的启动配置了
```
"scripts": {
　　"serve": "vue-cli-service serve",
　　"build": "vue-cli-service build",
　　"lint": "vue-cli-service lint"
}
```
