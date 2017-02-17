## 介绍
PHP rich app 是一套基于 CodeIgniter 的轻量级 PHP MVC 框架，用于团队快速开发 CMS 和 RESTful 规范接口服务。参照已有模块规范创建数据库表，编写模型、控制器、视图，就可以轻松扩展一个业务模块。

## 项目地址
出于安全性考虑，本项目不开源。地址：https://git.oschina.net/zhaojintian/cms 。

## 官网
https://www.richapp.cn/

## 案例
https://www.zjt.me/

## 下载代码
```
git clone https://git.oschina.net/zhaojintian/cms.git
```

## 业务模块
- 分类（categories）
- 文章（articles）
- 文件（files）
- 商铺（shops）
- 商品（commodities）
- 订单（orders）
- 岗位（jobs）
- 会员（users）
- 管理员（managers）。

## redis 缓存
框架采用 redis 来减轻数据库访问压力，如果当前服务器的 PHP 环境未安装 redis 扩展，则不启用 redis 缓存。注意，如果访问页面响应时间较长，请检查服务器是否已启动 redis 服务。

## 移动端检测
在控制器构造方法中调用 $this->_detect(); 可识别当前访问是否是来自移动端，并做相应跳转。

## 访问图片文件
```
/images/1              [访问 ID 为 1 的图片]
/images/1?w=200&h=300  [访问 ID 为 1 的图片，并按高度 200、宽度 300 等比缩放]
```

## 配置
修改 application/config/constants.php。

#### 文件 CDN 域名
为空时，启用当前网站域名，建议可以用七牛存储前端文件，如配置为：http://cncdn.cn/mydomain.cn 。
```php
define('CDN', '');
```
#### 静态文件版本号
静态文件变更时，需修改此配置，以清除浏览器缓存。
```php
define('STATIC_VERSION', 'v1.1');
```
#### redis 过期时间
配置 redis 缓存过期时间，单位为：秒。
```php
define('REDIS_EXPIRE', 60);
```

## 数据库
categories 为可选的通用分类表，每个业务模块都可以引用，用 model 字段来区分业务模块。  
数据库通用字段：
```
id         [自增 ID]
language   [语言标识，开发国际化项目时有用]
created_at [发布时间]
updated_at [更新时间]
```

## RESTful API 服务
如果接口需要鉴权，请在方法开头添加代码：
```php
if (!$this->_valid()) {
  $this->_responseValidError();
} else {
  // do something.
}
```

## 模型
```php
/**
 * 文章模型
 */
class Articles_Model extends MY_Model
{
  /**
   * 构造方法
   */
  function __construct()
  {
    parent::__construct(array(
      'table' => 'articles'
    ));
  }
}
```

## 控制器
待续

## 视图
待续
