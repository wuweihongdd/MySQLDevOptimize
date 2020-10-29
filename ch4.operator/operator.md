# MySQL中的运算符

## 算术运算符
|运算符|作用|
|:---|:---|
|+|加法|
|-|减法|
|*|乘法|
|/,DIV|除法|
|%,MOD|求模|

示例：
```sql
mysql> desc operator;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| eng_score  | decimal(4,1) | YES  |     | NULL    |       |
| math_score | decimal(4,1) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
2 rows in set (0.00 sec)
mysql> select eng_score+math_score as score_sum, (eng_score+math_score)/2 as score_ave, eng_score-math_score as eng_math from operator;
+-----------+-----------+----------+
| score_sum | score_ave | eng_math |
+-----------+-----------+----------+
|     164.4 |  82.20000 |    -13.6 |
|     142.8 |  71.40000 |    -36.8 |
|      89.2 |  44.60000 |     19.2 |
|     155.0 |  77.50000 |    -43.0 |
+-----------+-----------+----------+
4 rows in set (0.00 sec)

```

## 比较运算符
MySQL所支持的比较运算符

|运算符|作用|
|:---|:---|
|=|等于|
|<>,！=|不等于|
|<=>|NULL安全的等于|
|<|小于|
|<=|小于等于|
|>|大于|
|>=|大于等于|
|BETWEEN|存在于指定范围|
|IN|存在于指定集合|
|IS NULL|为NULL|
|IS NOT NULL|不为NULL|
|LIKE|通配符匹配|
|REGEXP或RLIKE|正则表达式匹配|

比较运算符可以用于比较数字 字符串和表达式。数字作为浮点数比较，字符串以不区分大小写的方式进行比较。

NULL不能用于"<>"和"="比较。
LIKE 运算符的使用格式为"a LIKE %123%",当a中含有字符串"123"时，返回值为1，否则返回0。

"REGEXP"运算符 的使用格式为"str REGEXP str_pat"。

针对，<=>与=的区别的示例：
```sql
mysql> select null=null;
+-----------+
| null=null |
+-----------+
|      NULL |
+-----------+
1 row in set (0.00 sec)

mysql> select null<=>null;
+-------------+
| null<=>null |
+-------------+
|           1 |
+-------------+
1 row in set (0.00 sec)

mysql> select 1=1;
+-----+
| 1=1 |
+-----+
|   1 |
+-----+
1 row in set (0.00 sec)

mysql> select 1<=>1;
+-------+
| 1<=>1 |
+-------+
|     1 |
+-------+
1 row in set (0.00 sec)
```

## 逻辑运算符
逻辑运算符用来确认表达式的真假。

MySQL中的逻辑运算符

|运算符|作用|
|:---|:---|
|NOT或!|逻辑非|
|AND或&&|逻辑与|
|OR或双竖线 |逻辑或|
|XOR|逻辑异或|

1. NOT或！表示逻辑非，返回和操作数相反的结果：操作数位0(假)，返回值位1，否则值位0.有一点除外，NOT NULL的返回值位NULL。
2. AND或&&表示逻辑与。当所有操作数均为非0值且不为NULL，计算结果为1，否则结果为0.
3. OR或||表示逻辑或。当两个操作有一个为NULL，如另一个操作数为非零值，结果为1，否则结果为NULL。如果两个操作数都是NULL，所得结果为NULL。

## 位运算符
将给定的操作数转换为二进制数，对各个操作数每一位都进行指定的逻辑运算，得到的二进制结果转换为十进制数后就是位运算的结果。

|运算符|作用|
|:---|:---|
|&|位与|
|单竖线|位或|
|^|位异或|
|~|位取反|
|>>|位右移|
|<<|位左移|