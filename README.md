## 介绍
PHP rich app 是一套基于 CodeIgniter 的轻量级 PHP MVC 框架，用于团队快速开发 CMS 和 RESTful 规范接口。

## 项目地址
出于安全性考虑，本项目不开源，地址：https://git.oschina.net/zhaojintian/cms 。

## 下载代码
```
git clone https://git.oschina.net/zhaojintian/cms.git
```

## 配置
修改 application/config/constants.php。

#### 文件 CDN 域名
为空时，启用当前网站域名，建议可以用七牛存储前端文件，如配置为：http://cncdn.cn/app.cn 。
```php
define('CDN', '');
```

// 静态文件版本号
define('STATIC_VERSION', 'v1.1');
// 输出缓存过期时间，单位 s
define('OUTPUT_CACHE_EXPIRE', 600);
// redis 过期时间，单位 s
define('REDIS_EXPIRE', 60);
