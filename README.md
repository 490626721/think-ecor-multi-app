# think-multi-app

用于ThinkPHP6+的多应用支持,支持在根目录下创建新目录作为额外应用目录

## 安装

~~~
composer require topthink/think-multi-app
~~~

## 使用

*   1.在 config/app.php 文件中配置:
```php
 // 指定根目录下额外目录为应用目录
    'extra_app'     => "system"
```
*   2.复制app目录至system目录下，并修改该目录下所有文件的命名空间为`system`

*   3.修改composer.json文件，将`autoload`下的`psr-4`配置为：
```json
"autoload": {
        "psr-4": {
            "app\\": "app",
            "system\\": "system" // 这里为上面配置的额外应用目录名
        },
        "psr-0": {
            "": "extend/"
        }
    },
```
*   4.在系统根目录下执行composer命令：

```composer
composer dump-autoload
```

#### 配置完成即可直接在system目录下创建新的应用目录，例如：admin；访问地址：http://localhost/admin/index


