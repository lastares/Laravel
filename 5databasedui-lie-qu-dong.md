```
1.修改驱动为database
①.env文件修改队列驱动：QUEUE_DRIVER=database

2.创建database的queue表
①php artisan queue:table 
②命令执行后在database/migrations目录下会多出一个迁移配置jobs表的文件,进行迁移

3.创建任务message
①php artisan make:job SendMessage
②此时在app\Jobs目录下会多出SendMessage.php文件，修改它
<?php

namespace App\Jobs;

use Illuminate\Bus\Queueable;
use Illuminate\Queue\SerializesModels;
use Illuminate\Queue\InteractsWithQueue;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Foundation\Bus\Dispatchable;
use App\Notice;

class SendMessage implements ShouldQueue
{
    use Dispatchable, InteractsWithQueue, Queueable, SerializesModels;


    /**
     * Create a new job instance.
     *
     * @return void
     */
    private $notice;
    public function __construct(Notice $notice)
    {
        $this->notice = $notice;
    }

    /**
     * Execute the job.
     *
     * @return void
     */
    public function handle()
    {
        // 通知每个用户的系统消息
        $users = \App\User::all();
        foreach($users as $user)
        {
            $user->addNotice($this->notice);
        }
    }
}



4.创建发送逻辑dispatch
/**
 * Store a newly created resource in storage.
 *
 * @param  \Illuminate\Http\Request  $request
 * @return \Illuminate\Http\Response
 */
public function store(Request $request)
{
    //验证
    $this->validate(request(), [
        'title' => 'required|min:2',
        'content' => 'required'
    ]);

    $notice = Notice::create(request(['title', 'content']));

    //队列分发逻辑 
    dispatch(new \App\Jobs\SendMessage($notice));
    return redirect('/admin/notices');
}

5.启动队列

php artisan queue:work --daemon
队列常驻进程:
①nohup php artisan queue:work >> /dev/null &
②使用supervisior

③Linux下
nohup

php artisan queue:listen &

```



