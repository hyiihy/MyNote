# <center> Json </center>

## 杂

从结构上看，所有的数据最终都可以分成三种类型：

- 第一种类型是scalar（**标量**），也就是一个单独的string（字符串）或数字（numbers），比如"北京"这个单独的词。
- 第二种类型是sequence（**序列**），也就是若干个相关的数据按照一定顺序并列在一起，又叫做array（数组）或List(列表)，比如"北京，东京"。
- 第三种类型是mapping（**映射**），也就是一个名/值对（Name/value），，比如"首都：北京"。

json简单说就是javascript中的对象和数组<br>
对象在js中表示为"{}"括起来的内容，数据结构为 {key：value,key：value,...}的键值对的结构<br>
数组在js中是中括号"[]"括起来的内容，数据结构为 ["java","javascript","vb",...]

## 语法规则

- 数据在键值对中
- 数据由逗号分隔
- 花括号保存对象
- 方括号保存数组

## Json值

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在方括号中）
- 对象（在花括号中）
- null

## 示例

- 数组型
  ```json
  [["北京市"],["上海市"],["合肥市","芜湖市","蚌埠市"]]
  ```

- 对象型
  ```json
  {"firstName":"Brett","lastName":"McLaughlin","email":"aaaa"}
  ```

- 复合型
```Json
{
    "people":[
        {"firstName":"Brett","lastName":"McLaughlin","email":"aaaa"},
        {"firstName":"Jason","lastName":"Hunter","email":"bbbb"},
        {"firstName":"Elliotte","lastName":"Harold","email":"cccc"}
    ]
}
```
