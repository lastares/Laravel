```
解决办法：
在vendor包内找到Builder.php这个文件，路径为vendor/laravel/framework/src/Illuminate/Database/Eloquent/Builder.php,然后在到1185行进行修改，修改如下
将
$originalWhereCount = count($query->wheres);
修改为

$originalWhereCount = 0;
if(is_array($query->wheres)) {
    if(count($query->wheres) > 0) {
    $originalWhereCount = count($query->wheres);
    }
}
```



