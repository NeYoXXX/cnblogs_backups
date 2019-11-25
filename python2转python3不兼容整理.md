记录遇到的python2与python3不兼容的地方，**给大家提供方便**。大家有知道哪些不兼容的地方，写到评论里我会及时更新到文章中。

**MySQLdb**      
MySQLdb 只适用于python2.x，发现pip3装不上。 它在py3的替代品是:pymysql，但python2的项目在python3运行会出现“没有安装MySQLdb”的错误需要在报错代码行之前加入以下代码：
```
 import pymysql
 pymysql.install_as_MySQLdb()
 ```

 **string 模块**    
python2代码：
```
string.uppercase
string.lowercase
```
python3代码：
```
string.ascii_uppercase
string.ascii_lowercase
```

**cStringIO与io**   
python2导入：
```
from cStringIO import StringIO
```
python3导入：
```
from io import StringIO
```

**xrange()函数**    
在python2中xrange() 函数用法与 range 完全相同，所不同的是生成的不是一个数组，而是一个生成器。
在python3中弃用了 xrange() 函数，用range()函数代替，在python3中range()函数生成一个生成器，而不是数组。

**StringIO()**
生成PIL图片验证码时，出现“TypeError: string argument expected, got 'bytes'”的错误。解决方案是：使用BytesIO()代替
```
#out = StringIO() 
#python3新增了bytes的数据类型
out = BytesIO()
```


