（1）在你的app/Providers/ServiceProvider.php中添加

```
\Carbon\Carbon::setLocale('zh');
```

这一行到boot\(\)方法当中，（为了中文化显示）



`public function boot()`

`{`

`    \Carbon\Carbon::setLocale('zh');`

`}`



