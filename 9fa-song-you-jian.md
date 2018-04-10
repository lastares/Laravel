```
1.配置.env文件
MAIL_DRIVER=smtp
MAIL_HOST=smtp.qq.com
MAIL_PORT=587
MAIL_USERNAME=862761213@qq.com
MAIL_PASSWORD=gncmdxbmzqlebeec(这里的密码连接邮件服务器的密码需要手动去配置，如QQ，则需要去QQ邮箱的账户去设置)
MAIL_ENCRYPTION=tls

2.编辑config/mail.php
'from' => [
        'address' => env('MAIL_FROM_ADDRESS', '862761213@qq.com'),
        'name' => env('MAIL_FROM_NAME', '凯恩书店'),
    ],

3.发送邮件
$uuid = UUID::create();
$m3Email = new M3Email;
$m3Email->to = $email;
$m3Email->cc = '862761213@qq.com';
$m3Email->subject = '凯恩书店验证';
$m3Email->content = '请于24小时内点击链接完成验证，http:://www.bookshop.com/service/validate_email'
                    . '&member_id=' . $member->id
                    . '&code=' . $uuid;
Mail::send('email_register', ['m3Email' => $m3Email], function($m) use ($m3Email){
    $m->to($m3Email->to, '尊敬的用户')
      ->cc($m3Email->cc)
      ->subject($m3Email->subject);
});
```



