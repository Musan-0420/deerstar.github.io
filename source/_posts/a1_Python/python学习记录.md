---
title: python学习记录
date: 2019-04-20
tags: python
categories: python
toc: true
---

1. #### 爬取淘宝评论

1. ##### 使用selenium和webdriver打开chrome浏览器

`selenium.common.exceptions.WebDriverException: Message: Service chromedriver unexpectedly exited. Status code was: 1`  
下载[chromedriver](https://sites.google.com/a/chromium.org/chromedriver/downloads)，注意与版本对应  
其为一个.exe文件，将其放在在chrome的安装目录下(C:\Program Files (x86)\Google\Chrome\Application\)，然后再配置环境变量

1. ##### Windows不重启使环境变量修改生效

cmd命令提示符, set PATH=C: ，重新打开DOS窗口， echo %PATH%  即可看到改变

1. ##### selenium 自动化测试打开chrome时，chrome地址栏总是出现data:,

  a. 下载与Chrome版本匹配的webdriver
  b. 配置环境变量 或者 在代码里把路径参数写对  
    chrome官方例程：
    `driver = webdriver.Chrome('/path/to/chromedriver')  # Optional argument, if not specified will search path.`  
    `driver.get('http://www.google.com/xhtml');`  
    应用时：`chromedriver = "C:/Program Files (x86)/Google/Chrome/Application/chromedriver"`\

1. ##### 如果出现空白页，则是selenium没有登陆淘宝

![selenium打开淘宝](image/screenshot/2019-04-20-20-18-18.png)
淘宝反爬机制限制selenium登陆

手动打开chrome  `chrome.exe --remote-debugging-port=9222 --user-data-dir="C:\selenum\AutomationProfile"`
怎么绕过验证码呢？？