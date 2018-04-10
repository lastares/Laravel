### 调试工具Laravel Debugbar

（1）引入package包

```
composer require barryvdh/laravel-debugbar
```

安装完成后，在`config/app.php`中注册服务提供者到`providers`数组。

（2）在config/app.php的providers中添加一行注册，注册如下服务提供者

```
Barryvdh\Debugbar\ServiceProvider::class
```



