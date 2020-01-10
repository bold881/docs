<center><h1>Java核心技术卷一基础知识第10版</h1></center>

### 三、Java的基本程序设计结构

Java基本类型：Java包括8种基本类型，4种整型、2种浮点类型、1种字符类型、1种真值类型

| 类型  | 长度 |
| ----- | ---- |
| int   | 4    |
| short | 2    |
| long  | 8    |
| byte  | 1    |

整型前后缀：

* 长整型后缀L或者l
* 十六进制数值有前缀0x或0X，如0xCAFE
* 八进制前缀0，如010
* 二进制前缀0b或0B，如0b1001代表9（Java7开始）
* 数字字面量可以加_，如1_000_000代表一百万，方便阅读，编译器自动去除（Java7开始）

浮点数后缀及特殊值：

* float类型的后缀f或者F
* double的后缀为d或者D
* 3.14默认为double
* 正无穷大，Double.POSITIVE_INFINITY
* 负无穷大，Double.NEGATIVE_INFINITY
* NaN (not a number)
* 所有非数值认为是都不相同的，Double.isNaN检测是否为数字
* 浮点数计算有舍入误差，不适用于金融计算，应该使用BigDecimal类