（1）在你的app/Providers/ServiceProvider.php中添加

```
\Carbon\Carbon::setLocale('zh');
```

这一行到boot\(\)方法当中，（为了中文化显示）

```
public function boot()
{
    \Carbon\Carbon::setLocale('zh');
}
```

（2）在某个模型中添加getCreatedAtAttribute方法

```
  public function getCreatedAtAttribute($date)
    {
        if (Carbon::now() < Carbon::parse($date)->addDays(10)) {
            return Carbon::parse($date);
        }

        return Carbon::parse($date)->diffForHumans();
}
```



