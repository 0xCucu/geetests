#说明
官方给出的sdk调用方法过于复杂浪费开发时间，我就封装了一个调用非常简单的一个geetest包可以减少开发人员不少时间
***
#安装
1. `composer require laraveler/geetest`
2. 在config/app.php providers 数组里加入 `geetest\provider\geetestServiceProvider::class`
3. 执行 `php artisan vendor:publish`

***
#调用
```php
 use geetest\Facades\geetest;

```
异步验证:
```php
return geetest::init($request,function(){Auth::attempt([....])},function(){....});
```
>同步验证时此方法仅用来初始化
```php
return geetest::init($request);
```
必须注册路由方法为any
>初始化时需要注入$request对象，第二个参数为验证成功后需要做的动作,第三个参数为验证失败需要的动作
