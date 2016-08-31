# <center>Oracle</center>

## 杂

1. **ORA-00937: 非单组分组函数**<br>
  原因：select 列表项中除了包含聚合函数外，还包含了表的某些列，那么你将必须使用group by语句，否则语法通不过。

- **GROUP BY 语句**<br>
  group by 语句将结果集按某列相同的聚合在一起<br>
  如果查询的其余的列都相同，则只显示一条，这时结果集数量会减小<br>
  如果对多个列使用group by，那么结果集数量会增加<br>
  一般使用了聚合函数之后需要接Group by语句

- **DECODE函数** decode函数为oracle独有<br>
  主要作用：将查询结果翻译成其他值

  ```sql
  Select decode（columnname，值1,翻译值1,值2,翻译值2,...值n,翻译值n,缺省值）  
  From talbename  
  Where …
  ```

  其中columnname为要选择的table中所定义的column<br>
  含义解释：<br>
  decode(条件,值1,翻译值1,值2,翻译值2,...值n,翻译值n,缺省值)的理解如下：

  ```sql
  if （条件==值1） then return(翻译值1)
  elsif （条件==值2） then return(翻译值2)
  ......
  elsif （条件==值n） then return(翻译值n)
  else return(缺省值)
  end if
  ```

- **LEFT JOIN、RIGHT JOIN、FULL JOIN**  
  **左连接**  
  ```sql
  SELECT column_name(s)
  FROM table_name1
  LEFT JOIN table_name2
  ON table_name1.column_name=table_name2.column_name
  ```
  看on后面的条件，遍历左表的列，每有一个相等返回一条数据，不管右表是否为空  
  **右连接**  
  与左连接类似，看on后面的条件，遍历右表的列，每有一个相等返回一条数据，不管左表是否为空  
  **全连接**  
  看on后面的条件，遍历两边表的列，每有一个相等返回一条数据，不管另外一表是否为空（顺序？）

-  **ORA-01722: 无效数字**  
  一串数字，若不加引号，则被认为是整型。  
  输入参数为一串数字的字符型时，若不加引号，Oracle会自动转型。  
  但若是字符太长超过，超过最大整型表示范围，则报错（大雾）

- **oracle 截取字符(substr)**  
  `SUBSTR（string,start_position,[length]）``
  ```sql
  select * from ps025_unit where substr(unitid,7,3)<>'000'
  select unitid,substr(unitid,6,3)from ps025_unit
  ```

- **DUAL**  
  dual表是Oracle系统生成、维护的一张虚拟表  
  dual只有一行数据  
  我们可以通过它完成：  
  - 查看当前用户  
    `select user from dual`

  - 
