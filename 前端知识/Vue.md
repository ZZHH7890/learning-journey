<!--
 * @Author: joker.zhang
 * @Date: 2020-08-17 10:20:41
 * @LastEditors: joker.zhang
 * @LastEditTime: 2020-08-17 19:10:10
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

## 配置vue
```
cnpm install -g vue-cli
```

```
$ vue -V
2.9.6
```

```
#这里需要进行一些配置，默认回车即可
vue init webpack my-project
```

```
cd my-project
cnpm install
cnpm run dev
```

## 配置axios
```
cnpm install --save axios 
```
main.js
```
import axios from 'axios'
Vue.prototype.axios = axios
```
也可以使用vue-axios
```
cnpm install --save axios vue-axios
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