# SELECT

- 查询语句：SELECT DISTINCT vend_id,prod_id FROM products LIMIT 0,2;
- DISTINCT表示返回不同的语句，LIMIT限制返回的语句，从0开始

# ORDER BY

- 对语句排序：SELECT DISTINCT vend_id,prod_id FROM products ORDER BY vend_id,prod_id;
- 指定降序用DESC，作用域为前面的一个列，默认升序
- 排序多个时，先排序前面的

# WHERE

- 过滤语句：SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price=2.5 ORDER BY prod_price;
- 排序语句要位于后面
- 操作符有等于，不等于，大于，大于等于，小于等于，小于，BETWEEN，<>，IS NULL
- <>也是不等于，BETWEEN配合AND ，表示某个区间
- SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price BETWEEN 5 AND 10 ORDER BY prod_price;
- IS NULL表示为空

# 组合WHERE

- AND，组合多个条件：SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price BETWEEN 5 AND 10 AND prod_id='FB';
- OR，表示任一条件：SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price BETWEEN 5 AND 10 OR prod_id='FB';
- 优先处理AND
- IN，指定条件范围：SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price BETWEEN 5 AND 10 OR prod_id IN ('FB','OL1');
- NOT ，表示否

# 通配符LIKE

- %，接收任意字符：jet%，表示接受以jet开头的词，可处于任意位置，接受0，1，多个字符
- SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price LIKE '5%';
- _，类似%，但是只匹配一个字符，不能多也不能少
- SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price LIKE '5.9_';
- 能不用就不用

# 正则表达式

- REGEXP，表示后面的字符串是个正则表达式：SELECT DISTINCT vend_id,prod_id,prod_price FROM products WHERE prod_price REGEXP '99';
- .匹配任意一个字符
- |表示或，匹配任一串，这个串或者那个串：‘9|10’
- [1234567890]，匹配从0-9的任一数字
- [^1234567890]，匹配除0-9外的串
- 上诉可以简化为[0-9]
- 特殊字符用\\，是的，两个\，一般语言用一个
- 匹配字符类，就是预先定义的一些字符，比如[:digit:]就是任意数字，同[0-9]
- 匹配多个串，*表示0或多个匹配，+表示1个及以上匹配，？表示0或者1个匹配，{n}表示n个匹配，{n,}表示n及n以上，{n,m}表示n到m
- 多个字符匹配的都是它的前一个字符，匹配四位数字：[[:digit:]]{4}
- 定位符，^文本的开始，$文本的结束，[[:<:]]词的开始，[[:>:]]词的节俗

# 创建计算字段

- Concat()，拼接字段：SELECT Concat(vend_name,'(',vend_country,')') FROM vendors ORDER BY vend_name;
- RTrim()，LTrim()，Trim()分别是去除串右边的空格，左边的空格，左右两边的空格
- 别名，AS：SELECT Concat(vend_name,'(',vend_country,')') AS t FROM vendors ORDER BY vend_name;
- 算术运算

# 数据处理函数

- 文本处理函数
- 日期和时间处理函数
- 数值处理函数

# 汇总数据

- AVG()
- COUNT()
- MAX()
- MIN()
- SUM()
- 上诉函数可以使用DISTINGCT参数，即只统计不同的值，该关键字放在列名前面，无需逗号分隔
- SELECT可以用多个以上函数

# 分组数据

- 