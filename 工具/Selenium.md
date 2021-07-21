<!--
 * @Author: joker.zhang
 * @Date: 2021-04-19 15:11:36
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-07-21 10:23:58
 * @mail: zhanghua7890@163.com
 * @Description: For Automation
-->
# Issues
## 清空输入框clear()失效问题解决
* [参考](https://www.cnblogs.com/yoyoketang/p/11516138.html)
* 思路1：双击输入框，全选原来的内容，即可输入了，都不用清空输入框了
* 思路2：万能JS大法，JS清空文本框 js = 'document.querySelector("XXXX").value="";'
* 思路3：直接再向输入框输入空内容

## 运行提示'use options instead of chrome_options'**
```
============================== warnings summary ===============================
TestCases/UI/updatecarrier/www/test_www.py::TestWWW::test_www[China-190260-http://www.hx-ep.com/-HXLEK0190103001YQ-\u5e7f\u5dde\u6c47\u7fd4-UCD]
  D:\mysoftware\python\lib\site-packages\selenium\webdriver\chrome\webdriver.py:50: DeprecationWarning: use options instead of chrome_options
    warnings.warn('use options instead of chrome_options', DeprecationWarning)

```
* 解决
只需要chrome_options改成options即可https://www.cnblogs.com/mengyu/p/9706770.html
```
 def __init__(self, browser=os.environ.get('Browser','Error:Browser')):
        logger.info("正在打开%s浏览器", browser)
        if browser == "Firefox" or browser == "firefox" or browser == "FireFox" or browser == "FF":
            driver = webdriver.Firefox()              
        elif browser == "Chrome" or browser == "chrome" or browser == "C":
            driver = webdriver.Chrome(options=OperateBrowser.set_chrome_options())
        elif browser == "IE" or browser == "ie" or browser == "I":  
            driver = webdriver.Ie()
        elif browser == "Edge" or browser == "edge" or browser == "E":
            driver = webdriver.Edge()
        else:
            print("can not open browser:"+browser) 
        try:
            self.driver = driver
            self.driver.maximize_window()
        except Exception as msg:
            logger.info("打开%s浏览器失败-->><%s>", browser, msg)
```

## 跑selenium的时候，谷歌浏览器打开会出现‘Chrome 正在受到自动化软件控制’**

* 解决方法一:在代码里面直接添加谷歌设置disable-infobars

```
option = webdriver.ChromeOptions()
option.add_argument('disable-infobars')disable-infobars
```


* 解决方法二:直接添加到webdriver的chrome中：python\Lib\site-packages\selenium\webdriver\chrome\options.py

```
class Options(object):
    KEY = "goog:chromeOptions"

    def __init__(self):
        self._binary_location = ''
        self._arguments = ['disable-infobars']
        self._extension_files = []
        self._extensions = []
        self._experimental_options = {}
        self._debugger_address = None
```

* 解决方法三: 谷歌浏览器升级到版本76之后，disable-infobars不生效了，找谷歌搜一下
https://github.com/GoogleChrome/puppeteer/issues/2070

https://help.applitools.com/hc/en-us/articles/360007189411--Chrome-is-being-controlled-by-automated-test-software-notification

```
option = webdriver.ChromeOptions()
option.add_experimental_option('excludeSwitches',['enable-automation'])
#option.add_argument('disable-infobars')
```

## selenium跑页面时，经常会遇到localstorage类型的弹窗**

* 解决
selenium没有直接处理localstorage的api, 所以需要通过js来预先设置好需要的localstorage的key和value，需要注意的是设置localstorage要在打开页面之前

```
self.input_url("https://*/global-v2/favicon.ico") #先随便设置localstorage所在域
js_h = 'localStorage.setItem("v6_gdpr", true);'
self.excecute_js(js_h)
```