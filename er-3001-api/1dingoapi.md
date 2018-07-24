[dingo/api](https://github.com/dingo/api/)是一个 Lumen 和 Laravel 都可用的 RestFul 工具包，帮助我们快速的开始构建 RestFul Api。我们的目的是教会大家如何快速的搭建并使用这个包，更多的功能，还需要你仔细阅读 DingoApi 的[文档](https://github.com/dingo/api/wiki)来深入的学习和理解，[这里](https://github.com/liyu001989/dingo-api-wiki-zh)有一份中英对照的翻译，或许能帮到你。

1.安装

Laravel 5.5 的适配版本为\```dingo/api:v2.0.0-alpha2```，所以我们需要安装这个 tag

```
composer require dingo/api:2.0.0-alpha2
```

dingo 的文档中有说明，现在这个包还处在开发阶段，没有一个稳定的 release 版本，dingo/api 依赖的

``dingo/blueprint`与``\```phpuni`都依赖了`phpdocumentor/reflection-docblock```

但是依赖的版本不同，导致出现了冲突。但是我们发现\```dingo/blueprint`的开发版本`dev-master```

解决了冲突，可以正常安装，所以我们修改一下\``composer.json`\`：

```
.
.
.
    "config": {
        "preferred-install": "dist",
        "sort-packages": true,
        "optimize-autoloader": true
    },
    "minimum-stability" : "dev",
    "prefer-stable" : true
}
```



