# Java知识点
## 面向对象特征
## final, finally, finalize的区别
## int和Integer有什么区别
## 重载和重写的区别
### 重载(Overload)
* 不能以返回值类型来区分重载函数
### 重写(Override)
* 重写是子类对父类方法的重新实现，返回值和形参类型不能改变
* 重写不能抛出新的检查异常，不能声明比被重写方法更加宽泛的异常
* 方法重写访问权限不能比父类中被重写方法的权限更低（如父类public，子类不能位protected或者private）
* final的方法不能被重写，static不能被重写但是可以被再次声明
* 重写的方法可以抛出任何非强制性异常，不能抛出新的强制性异常，或者比被重写方法更广泛的强制性异常
* 构造方法不能被重写
* 如果不能继承一个方法，也不能重写一个方法
* super用于再重写的方法中调用被重写的父类的方法
## 抽象类和接口的区别
* 抽象类中的方法可以有具体的方法体，接口没有
* 抽象类中的成员变量可以是各种类型的，接口中只能是public static final类型，接口中方法只能是public abstract类型
* 接口中不能有静态代码块和静态方法，抽象类中可以有静态代码和静态方法
* 一个类只能继承一个抽象类，可以实现多个接口
## Java类的初始化顺序
* 静态代码块，并初始化静态变量
* 构造代码块，并初始化成员变量
* 构造函数初始化
## 继承体系初始化
* 执行父类的静态代码块，并初始化父类的静态变量
* 执行子类的静态代码块，并初始化子类的静态变量
* 父类的构造代码块，执行父类的构造函数，并初始化父类的普通成员变量
* 子类的构造代码块，执行子类的构造函数，并初始化子类的普通成员变量
## 为什么类只能继承一个父类，接口却可以多继承
* 接口中除了default方法外都是抽象方法，都需要在实现类中实现，所以可以避免冲突。多个类继承的话会存在方法冲突的情况。
## 常见的异常类型
* java.lang.NullPointerException 空指针异常
* java.lang.ClassNotFoundException 指定的类不存在
* java.lang.NumberFormatException 字符串转为数字异常
* java.lang.IndexOutOfBoundsException 字符串数据下标越界异常
* java.lang.IllegalArgumentException 方法的参数错误
* java.lang.IllegalAccessException 没有访问权限
* java.lang.ArithmeticException 数学运算异常
* java.lang.ClassCastException 数据类型转换异常
* java.lang.FileNotFoundException 文件未找到异常
* java.lang.ArrayStoreException 数组存储异常
* java.lang.NoSuchMethodException 方法不存在异常
* java.lang.NoSuchFieldException 域不存在
* java.lang.EOFException 文件已技术异常
* java.lang.InstantiationException  实例化异常，通过newInstance创建实例，实例化失败，如果接口或抽象类
* java.lang.InterruptedException 被中止异常 当某个线程处理等待、休眠或其他暂停状态，此时其他线程通过Thread.interrupt中止该线程时抛出
* java.lang.CloneNotSupportedException 不支持克隆异常，没有实现Cloneable接口或者不支持克隆方法时调用clone()时抛出
* java.lang.OutOfMemoryException 内存不足异常
* java.lang.NoClassDefFoundException 未找到类定义错误，JVM实例化某个类，找不到定义时抛出
* 