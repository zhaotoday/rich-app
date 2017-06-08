## 介绍
PHP rich app 是一套基于 CodeIgniter 的轻量级 PHP MVC 框架，用于团队快速开发 CMS、商城和 RESTful API 服务。参照已有模块规范创建数据库表，编写模型、控制器和视图，就可以轻松扩展一个业务模块。

## 项目地址
出于安全考虑，本项目不开源，仅团队开发人员可见。地址：https://git.oschina.net/zhaojintian/rich-app 。

## 官网
- https://www.richapp.cn/

## 案例
- https://www.zjt.me/

## 相关
- [CodeIgniter 中国](http://codeigniter.org.cn/)
- [CodeIgniter GitHub](https://github.com/bcit-ci/CodeIgniter)
- [codeigniter-restserver](https://github.com/chriskacerguis/codeigniter-restserver)
- [简易的 RESTful API 规范](https://github.com/zhaotoday/rest-api-guide)
- [codeigniter3-translations](https://github.com/bcit-ci/codeigniter3-translations)

## 下载代码
```
git clone https://git.oschina.net/zhaojintian/rich-app.git
```

## 业务模块
- 分类（categories）
- 标签（tags）
- 评论（comments）
- 文章（articles）
- 文件（files）
- 商铺（shops）
- 商品（commodities）
- 订单（orders）
- 岗位（jobs）
- 会员（users）
- 设置（settings）
- 管理员（managers）
- 滚动广告（sliders）

## Redis 缓存
框架采用 Redis 来减轻数据库访问压力，如果当前服务器的 PHP 环境未安装 Redis 扩展，则不启用 Redis。注意，如果访问页面响应时间较长，请检查服务器是否已启动 Redis 服务。

## 移动端检测
在 Front_Controller 的构造方法中调用 detect(); 可识别当前访问是否是来自移动端，并做相应跳转。

## 访问图片文件
```
GET /images/1              [访问 ID 为 1 的图片]
GET /images/1?w=200&h=300  [访问 ID 为 1 的图片，并按高度 200px、宽度 300px 等比缩放]
```

## 配置
修改 application/config/constants.php。

#### 静态文件 CDN 域名
为空时，启用当前网站域名，建议可以用七牛存储静态文件，如配置为：http://cncdn.cn/{domain}.cn 。
```php
define('CDN', '');
```

#### 静态文件版本号
静态文件变更时，需修改此配置，以清除浏览器缓存。
```php
define('STATIC_VERSION', 'v1.1');
```

#### Redis 过期时间
配置 Redis 过期时间，单位为：秒。
```php
define('REDIS_EXPIRE', 60);
```

## 数据库
categories 为可选的通用分类表，每个业务模块都可以引用，用 model 字段来区分业务模块。  
数据库通用字段：
```
id         [自增 ID]
language   [国际化语言标识]
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

## 表单校验
数据入库前，需校验合法性。  
#### 加载校验类  
```php
$this->load->library('Validator', NULL, 'validator');
```

#### 中文
```php
$this->validator->isChinese($test);
```

#### 邮箱
```php
$this->validator->isEmail($test);
```

#### 身份证
```php
$this->validator->isIDCard($test);
```

#### 手机
```php
$this->validator->isMobilePhone($test);
```

#### 电话
```php
$this->validator->isTelephone($test);
```
#### IP
```php
$this->validator->isIP($test);
```

#### 邮编
```php
$this->validator->isPostcode($test);
```

#### 长度不能小于
```php
$this->validator->min($test, $length);
```

#### 长度不能大于
```php
$this->validator->max($test, $length);
```

## 业务模块目录规范
以下以 Articles 模块为例。

#### 模型
```
application/models/Articles_Model.php
```

#### 前台控制器
```
application/controllers/Articles.php
```

#### API 控制器
```
application/controllers/apis/Articles.php
```
