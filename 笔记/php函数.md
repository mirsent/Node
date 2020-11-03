#### 替换手机号中间数字为*号

```php
$string = "13826589549";
$pattern = "/(\d{3})\d{4}(\d{4})/";
$replacement = "\$1****\$2";
print preg_replace($pattern, $replacement, $string);
```

#### 隐藏ip最后几位

```php
preg_replace("/[^\.]{1,3}$/","*",$ip);
```

