<!--
 * @Author: joker.zhang
 * @Date: 2021-04-19 15:11:36
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-07-21 10:23:58
 * @mail: zhanghua7890@163.com
 * @Description: For Automation
-->
# 原理
## selenium到底怎么工作
(参考)[https://www.lmlphp.com/user/3173/article/item/27008/]selenium的工作主要分为3个角色
* 我们的自动化代码，可以是python/java/c#等，对应技术上的是WebDriver API：自动化代码发送请求给浏览器的驱动，也就是对于每一条Selenium脚本，一个http请求会被创建并且发送给浏览器的驱动
* 浏览器驱动,对应技术上chromedriver.exe/geckodriver.exe/IEDriverServer.exe：它来解析这些自动化测试的代码，解析后把它们发送给浏览器，也就是浏览器驱动中包含了一个用来接收这些http请求的HTTP Server ，它接收到请求后根据请求来具体操控对应的浏览器
* 浏览器，对应谷歌/火狐/IE等浏览器：执行浏览器驱动发来的指令，并最终完成工程师想要的操作，也就是浏览器执行具体的测试步骤然后浏览器将步骤执行结果返回给HTTP Server，HTTP Server又将结果返回给Selenium的脚本


## selenium工作原理详解
(参考)[https://www.cnblogs.com/linuxchao/p/linux-selenium-webdriver.html]
### 原理Demo
这个demo我跟着做了，运行成功了，但是response响应返回404了，还需要时间找找原因，当然我觉得这个demo很好的展示的selenium的工作原理sessionId
```python
import requests
# 请求地址(打开浏览器)
driver_url = 'http://localhost:9515/session'
# 打开浏览器的请求参数
driver_value = {"capabilities":
                    {"firstMatch": [{}],
                     "alwaysMatch":
                         {"browserName":
                              "chrome",
                          "platformName": "any",
                          "goog:chromeOptions":
                              {"extensions": [], "args": []}}},
                "desiredCapabilities":
                    {"browserName":
                         "chrome",
                     "version": "",
                     "platform": "ANY",
                     "goog:chromeOptions": {"extensions": [],
                                            "args": []}}}
# 发送求清
response_session = requests.post(driver_url, json = driver_value)
print(response_session.json())
url = 'http://localhost:9515/session/'+response_session.json()['sessionId']+'/url'
# 访问我的博客的请求参数
value = {"url": "https://www.cnblogs.com/linuxchao/", "sessionId": response_session.json()['sessionId']}
response_blog = requests.post(url = url,json = value)
print(response_blog.json())
```
### 原理解释
* selenium client(python等语言编写的自动化测试脚本)初始化一个service服务，通过Webdriver启动浏览器驱动程序chromedriver.exe
* 通过RemoteWebDriver向浏览器驱动程序发送HTTP请求，浏览器驱动程序解析请求，打开浏览器，并获得sessionid，如果再次对浏览器操作需携带此id
* 打开浏览器，绑定特定的端口，把启动后的浏览器作为webdriver的remote server
* 打开浏览器后，所有的selenium的操作(访问地址，查找元素等)均通过RemoteConnection链接到remote server，然后使用execute方法调用_request方法通过urlib3向remote server发送请求
* 浏览器通过请求的内容执行对应动作
* 浏览器再把执行的动作结果通过浏览器驱动程序返回给测试脚本

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