```
在laravel中自己创建类
首先我们先创建一个文件夹来存放我们类库 
mkdir app/Libs
我们在这个文件夹下创建自己的类 
app/Libs/Demo.php
接着我们需要将这个类使用psr-4标准自动加载 
在项目的更目录的composer.json中"autoload-dev"里的"psr-4"添加"app\\Libs\\": "app/Libs/"
接着需要执行以下命令 
composer dump-autoload
这是我们找到 
vendor/composer/autoload_psr4.php中看是否多了 
'app\\Libs\\' => array($baseDir . '/app/Libs'),
接下来你就可以use App\Libs\Demo 
可以使用你在demo里写的方法了。
```



