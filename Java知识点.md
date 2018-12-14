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
* java.lang.SecurityException 在java.lang包下定义了一个类，加载时抛出违背安全原则异常
* java.lang.SQLException 数据库访问错误或其他错误
* java.lang.IOException 当I/O操作失败或者被中止时抛出
* java.lang.SocketException 创建和访问Socket通信出错时抛出
## Java的八种数据基本类型
* byte（字节型，1字节）
* short(短整型，2字节)
* int（整型,4字节）
* long（长整型，8字节）
* double（双精度浮点数，8字节）
* float（单精度浮点数，4字节）
* char（字符型，2字节）
* boolean（布尔型，1字节）
## equals和==的区别
* 值类型（基本数据类型）用==判断相等性
* == 判断引用所指的对象是否同一个
* equals是Object的成员函数，用于判断对象的等价性
## List和Set的区别
* List是有序放入，可以放入重复元素
* Set是无序放入，元素不可重复，重复会被覆盖（元素的hashcode决定，其实位置是固定的）
* List插入或删除时效率低，Set插入和删除时效率高，List的此操作会影响其他元素的位置，Set的此操作不会
* List支持for循环，可以用小标访问，可以用迭代访问元素，Set因为无序只能用迭代访问
## List和Map的区别
* List是对象集合，允许对象重复
* Map是键值对集合，key不允许重复
## ArrayList和LinkedList的区别
* ArrayList基于动态数组实现，在内存中是连续存放的，查询效率高，插入和删除效率低。
* LinkedList是基于链表的数据结构，add和remove效率比ArrayList高，适用于头尾和指定位置的插入操作
## ArrayList和Vector的区别
* ArrayList是非线程安全的，Vector是线程安全的
* 都是存储在连续空间的，空间扩容（增加元素）方式不一样，ArrayList不能设置增长因子为原数组长度的1.5倍，Vector为原数组长度+增加的素组长度，若为0，则新的长度为原来的两倍。
* 除去线程安全的因素，ArrayList的效率要高于Vector
## HashMap和HashTable的区别
* HashMap是非同步的，HashTable是同步的线程安全的
* HashMap接口移除了HashTable中的contains方法，增加了containsKey和containsValue方法
* HashMap的效率要高于HashTable
* HashMap的迭代器是fail-fast，HashTable不是。HashMap可能会抛出java.util.ConcurrentModificationException,迭代器本身的remove不会抛出此异常
* HashMap随着时间的推移不能保证元素的顺序不发生变化
* HashMap的键值可以为null，Hashtable不行
## 线程安全和同步
* 线程安全是指同一代码段，在多个线程和单个线程执行的情况下结果一致，其他变量的值也和预期的一样
* 线程同步是指同步多个线程的动作，确保在给定的时间点只有一个线程可以访问资源，使用称为监视器概念实现的。
## TreeMap
* TreeMap适用于按自然顺序或自定义顺序遍历键
## HashSet和HashMap的区别和共同点
* HashSet是线性结构，是set的Hash实现，值不能重复
* HashMap存储的是k，v的键值对，是map的Hash实现，键值不能重复
* 两种共同点是利用hash算法实现唯一性，不能存储基本数据类型，必须是对象
## 桶排序（bucket sort）
桶排序是将数组划分为大小相同的n个区间，每个区间各自排序，最后合并
## HashMap和ConcurrentHashMap的区别
* ConcurrentHashMap对整个桶数组进行了分割分段，在每一段上用lock锁进行保护，比HashTable的synchronized关键字锁粒度细，并发性能更高
* HashMap没有锁机制，不是线程安全的
* HashMap允许空的键值对，ConcurrentHashMap不允许
## 创建线程的三种方式
* 继承Thread类、实现Runnable接口和实现Callable接口
* 继承Thread类不能再继承其他类，实现Runnable和Callable接口可以继承其他类
* 继承Thread类直接使用this获取到当前线程，实现Runnable和Callable通过Thread.currentThread()获取当前线程对象
## sleep(), yield(), join()的区别
* sleep()让当前正在执行的线程休眠，让低优先级，同优先级，高优先级的其他线程有机会执行
* sleep()不会释放对象锁，如果有synchronized同步块，其他线程仍不能访问共享数据
* yield()不会释放对象锁，使当前线程回到可执行状态，yield()只会使同优先级和高优先级的线程获得执行机会
* join()把指定的线程加入到当前线程，可以把两个线程变为顺序执行，如线程b中调用a.join(),则b会在线程a执行完之后才会继续执行（jion可以传入等待时间）
## String，StringBuffer，StringBuilder的区别
* String 字符串常量
* StringBuffer 字符串变量 线程安全
* StringBuilder 字符串变量 非线程安全
* 大部分情况下StringBuffer > String (除了String a = "abc" + "def" + "ghk")
* 大部分情况下StrnigBuilder > StringBuffer
