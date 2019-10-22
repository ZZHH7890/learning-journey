<!--
 * @Author: joker.zhang
 * @Date: 2019-10-22 16:47:49
 * @LastEditors: joker.zhang
 * @LastEditTime: 2019-10-22 16:58:27
 * @Description: For Automation
 -->
# Issues


**1. 运行提示'use options instead of chrome_options'**
```
============================== warnings summary ===============================
TestCases/UI/updatecarrier/www/test_www.py::TestWWW::test_www[China-190260-http://www.hx-ep.com/-HXLEK0190103001YQ-\u5e7f\u5dde\u6c47\u7fd4-UCD]
  D:\mysoftware\python\lib\site-packages\selenium\webdriver\chrome\webdriver.py:50: DeprecationWarning: use options instead of chrome_options
    warnings.warn('use options instead of chrome_options', DeprecationWarning)

```
**解决：**
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

**2. 跑selenium的时候，谷歌浏览器打开会出现‘Chrome 正在受到自动化软件控制’**

**解决方法一**在代码里面直接添加谷歌设置disable-infobars

```
option = webdriver.ChromeOptions()
option.add_argument('disable-infobars')disable-infobars
```


**解决方法二**将disable-infobars不生效了，百度不行找谷歌搜索 直接添加到webdriver的chrome中：python\Lib\site-packages\selenium\webdriver\chrome\options.py

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

**解决方法三** 谷歌浏览器升级到版本76之后，disable-infobars不生效了，找谷歌搜一下
https://github.com/GoogleChrome/puppeteer/issues/2070

https://help.applitools.com/hc/en-us/articles/360007189411--Chrome-is-being-controlled-by-automated-test-software-notification

```
option = webdriver.ChromeOptions()
option.add_experimental_option('excludeSwitches',['enable-automation'])
#option.add_argument('disable-infobars')
```