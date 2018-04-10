##### 方法1

1.修改 composer.json 的 autoload 配置项，在 files 中加入要引入的自定义函数文件

`"autoload": {`

`	"files": [`

`	  "app/Helpers/functions.php"`

`	 ]`

`	 ...`

`	 ...`

`},`

2.composer 的 autoload\_files.php 文件，进入项目根目录执行下面命令

	`composer dump-autoload`



##### 方法2

1.在app 文件下 建立 fun.php文件, 在里面写自定义函数

    bootstrap 文件夹下的 autoload.php 文件中 加入一行:　require \_\_DIR\_\_.'/../app/fun.php';





