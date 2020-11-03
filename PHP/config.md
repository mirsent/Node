### PHP关闭warning

1. php页面头部

   ```php
   error_reporting(E_ERROR); 
   ini_set("display_errors","Off");
   ```

2. php.ini

   ```ini
   display_errors = Off
   error_reporting = E_ALL
   ```

   

