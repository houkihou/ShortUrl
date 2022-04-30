# 不用数据库的短网址

未使用数据库，利用php的数组保存数据，可以放二级文件夹使用
生成二维码改为jquery.qrcode.js
生成短网址的形式：默认是5位小写字母和数字，可选从1开始依次增加的数字


#### 使用说明

1、将所有文件复制到你的项目中。
 比方你的短网址域名为https://xxx.com/ ，那么放到https://xxx.com/ 对应的的目录

2、urls123.php和urlsabc.php文件需设置为777权限
 短缩网站地址会存放在该文件中，所以需要读写权限

3、修改config.php

```html
'title' => "短网址生成",                               //网站标题
'site' => "https://xxx.com/",                         //你的短网址域名
'blackList' => array('*.baidu1.com','youtube1.com'),  //不允许缩短的域名，单个匹配，*表示所有的二级域名
'key' => "idjl",                                      //token 使用的密钥

//根据需求修改
'use_rewrite' => 1,                                   // 是否使用伪静态,默认使用
//生成的短网址类型：abc表示字母数字混合，123为纯数字累加方式
'type' => 'abc',
```

4、访问你的短网址域名：https://xxx.com/


#### 伪静态的使用


默认开启伪静态，可以关闭，
config.php中修改'use_rewrite' => 2即可。

apache可以直接使用；
伪静态的使用：.htaccess文件内容如下
```php
RewriteEngine On
#RewriteBase / 
RewriteRule ^(\w+)$ create.php?id=$1
```




