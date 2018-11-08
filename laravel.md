# Laravel 学习笔记

## composer

[官网](https://getcomposer.org/)
[中文网](http://www.phpcomposer.com/)
[插件库](https://packagist.org/)

切换国内镜像：`composer config -g repo.packagist composer https://packagist.phpcomposer.com`

安装单个扩展包命令：`composer require 作者名/扩展包名;`

安装完成的项目命令：`composer create-project 作者名/项目名;`

## laravel

### 安装

#### 通过 Laravel 安装器

使用 Composer 下载 Laravel 安装程序：

`composer global require "laravel/installer"`

`laravel new` 命令会在你指定的目录中创建一个新的 Laravel 项目

`laravel new blog`

#### 通过 Composer 创建项目

`composer create-project --prefer-dist laravel/laravel blog "5.5.*"`

#### 应用密钥

`php artisan key:generate`

### route

利用 group prefix middleware 让路由更简洁和更有层级感

```php
// Admin 模块
Route::group(['namespace' => 'Admin', 'prefix' => 'admin', 'middleware' => 'admin.auth'], function () {
    // 文章管理
    Route::group(['prefix' => 'article'], function () {
        // 文章列表
        Route::get('index', 'ArticleController@index');
        // 发布文章
        Route::get('create', 'ArticleController@create');
        // ...
    });

    // 分类管理
    Route::group(['prefix' => 'category'], function () {
        // 分类列表
        Route::get('index', 'CategoryController@index');
        // 添加分类
        Route::get('create', 'CategoryController@create');
    });
});
```

### 配置

时区 -> PRC； locale -> zh-ZN；

### controller

创建控制器：
```php
php artisan make:controller ControllerName
php artisan make:controller ControllerName --resource
```

### 迁移文件

建立迁移文件：

```php
php artisan migrate:make create_users_table
php artisan migrate
```

> 创建表： `Schema::create`
> 编辑表： `Schema::table`

### model

models 目录用于存放与数据库交互的模型类


```php
DB('users')
    ->select('id', 'user_name', 'user_password')
    ->where('id', 1)
    ->groupBy('user_name')
    ->orderBy('id', 'desc')
    ->having('id', '>', 5)
    ->limit(10)
    ->get(); // 得到一个 Collection 对象
```

创建模型：

```php
php artisan make:model ModelName
```

创建模型同时建立迁移文件：

```php
php artisan make:model Models/ModelName -m
```

### view

`yield` `section`

给前端home模块分配数据：
在/app/Providers/AppServiceProvider.php 文件的 boot 中

```php
// 分配前台通用的 category 数据
view()->composer('home/*', function ($view) {
    // 获取配置项
    $category = Category::all();
    $assign = [
        'category' => $category
    ];
    $view->with($assign);
});
```

控制器中分配数据:
```php
public function index()
{
    $article = Article::all();
    $category = Category::all();
    $tag = Tag::all();
    $assign = compact('article', 'category', 'tag');
    return view('home.index.index', $assign);
}
```

### 自定义函数和类

自定义函数：

`composer.json`在`autoload`中加上`files`


自定义类：

`composer.json`在`autoload` `classmap` 加上 `app/Libraries/Org`

```json
"autoload": {
    "classmap": [
        "database",
        "app/Libraries/Org"
    ],
    "psr-4": {
        "App\\": "app/"
    },
    "files": [
        "app/Libraries/Functions/helpers.php"
    ]
},
```
运行更新命令：`composer dump-autoload`


控制器中的方法返回页面或者redirect都必须要 return ；

`view` 函数定位到 `resources/views` 目录；
`env` 函数获取 `.env` 配置 : `'name' => env('APP_NAME', 'Laravel')` 
第一个参数是配置项名，第二个参数是默认值；
