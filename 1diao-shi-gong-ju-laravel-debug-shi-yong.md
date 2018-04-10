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

（3）如果你想使用门面，在配置文件`config/app.php`中添加如下门面别名到`aliases`数组

```
'Debugbar' => Barryvdh\Debugbar\Facade::class,
```

（4）运行如下 Artisan 命令将该扩展包的配置文件拷贝到`config`目录下

```
php artisan vendor:publish
```

#### **Lumen** {#ipt_kb_toc_2774_3}

对于 Lumen 而言，在`bootstrap/app.php`中注册服务提供者：

```
if (env('APP_DEBUG')) {
    $app->register(Barryvdh\Debugbar\LumenServiceProvider::class);
}
```

要修改默认配置，将配置文件拷贝到`config`目录并做相应修改：

```
$app->configure('debugbar');
```



