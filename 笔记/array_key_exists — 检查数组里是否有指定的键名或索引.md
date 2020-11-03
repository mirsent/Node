### array_key_exists — 检查数组里是否有指定的键名或索引

```php
array_key_exists ( mixed $key , array $array ) : bool	
```

数组里有键 `key` 时，**array_key_exists()** 返回 **`TRUE`**。 `key` 可以是任何能作为数组索引的值。key



#### 参数

------

```
key
```

要检查的键。

```
array
```

一个数组，包含待检查的键。

#### 返回值

------

成功时返回 **`TRUE`**， 或者在失败时返回 **`FALSE`**

> **array_key_exists()** 仅仅搜索第一维的键。 多维数组里嵌套的键不会被搜索到。

#### 范例

```php
<?php
$search_array = array('first' => 1, 'second' => 4);
if (array_key_exists('first', $search_array)) {
    echo "The 'first' element is in the array";
}
?>		
```

##### array_key_exists() 与 [isset()](https://www.php.net/manual/zh/function.isset.php) 的对比

[isset()](https://www.php.net/manual/zh/function.isset.php) 对于数组中为 **`NULL`** 的值不会返回 **`TRUE`**，而 **array_key_exists()** 会。

```php
<?php
$search_array = array('first' => null, 'second' => 4);

// returns false
isset($search_array['first']);

// returns true
array_key_exists('first', $search_array);
?>
```

