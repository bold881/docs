# Java设计模式

### 挑战1 

接口和抽象函数的区别：

1. 接口的方法都是public，抽象函数的方法可以是public, private, protected或者默认的package
2. 抽象发放可以定义实例变量、接口只能定义静态变量
3. 一个类可以实现多个接口，只能继承一个抽象类
4. 抽象类可以包含具体的方法，但接口的方法都是抽象的

### 挑战2

1. 接口中的方法都是抽象方法（8之后interface可以有默认实现）
2. 接口中的方法都是公开方法
3. 接口必须被显示的标记为public才能被包外的类访问
4. 接口可以被扩展一次
5. 接口可以没有方法
6. 接口不能声明实例字段

### 对象适配器和类适配器

