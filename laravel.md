# Laravel

composer安装laravel：

```php
composer create-project laravel/laravel your-project-name --prefer-dist
```

建立迁移文件：

```php
php artisan migrate:make create_users_table
php artisan migrate
```

创建模型：

```php
php artisan make:model ModelName
```

创建模型同时建立迁移文件：

```php
php artisan make:model Models/ModelName -m
```

创建控制器：
```php
php artisan make:controller ControllerName
php artisan make:controller ControllerName --resource
```


models 目录用于存放与数据库交互的模型类

```php
php artisan make:model Models/Test
```

控制器中的方法返回页面或者redirect都必须要 return