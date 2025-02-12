# Java部分

## ***一.方法(程序最小执行单元)***

*1.修饰方法的关键字static*

- static method(静态方法)：整个class共享的method
- ###### non-static method(非静态方法): 具体实例的method-----***就是要有对象  调用也是"对象.方法名()"***

*2.方法重载*

- 方法名相同,参数不同,**与返回值无关**
- **好处: ** 定义方法和调用方法更简单




## ***二.面向对象***

1.封装

- 简单理解：将对象***特有属性***封装进去

2.private关键字

- 只能在本类中访问

  赋值可如下操作

  ```java
  public class Girl{
  private int age;
      //给年龄赋值
      public void setAge(int a){
          if(a>=18&&a<=50){age=a;}
          else{sout("非法");}
      //获取年龄
      public int getAge(){
          return age;
         }
  }
  ```

3.成员变量(**方法外类里面**)和局部变量(**测试类中调用方法传递过来的数据**)

- 当成员变量和局部变量同名时, 对于类里定义的方法使用哪个, 则采取***就近原则*** ;

- ***this***关键字修饰, 指定使用成员变量 ; 如下 :

  ```java
      public int getAge(){
          return this.age;
         }
  ```

4.构造方法 (**空参**和带全部参构造,其中空参是默认的)

- 修饰符 类名(参数) {

  方法体

  }

- 没有<u>返回值</u> (void都不能)

- 快捷键 alt+insert 或者alt + fn+insert

- 插件--PTG--Javabeans

- 创建对象时---------**new 类名()** 可以当返回值使用

## ***三.面向对象（高级）***

### 1.继承（子父类关系）

- 方法：public class 子类名 extends 父类名 {}
- 作用：子类可以使用父类非私有的成员
- 特点：支持单继承和多层继承，成员变量重名时用**就近原则**，***如果要访问父类则使用super关键字修饰***

### 2.方法重写（覆盖）

- 概述：子类方法名和参数与父类完全一致

  

  ***注意：*** *1*.父类私有方法不能重写，子类重写权限大于等于父类   

​                  *2*.构造方法继承不了，但是

​                  Java  **<u>所有构造方法可以看成默认有super()</u>**-----------另一个理解就是Java所有类的祖宗是java的object类

​                  所以，子类初始化时一定先完成父类初始化（即默认调用父类空参构造方法）

​                  3.如果父类没有空参构造但是有有参构造，则子类构造调用super（参数）有参构造即可

### 3.super和this

- super--父类对象引用
- this--本类对象引用

### 4.final关键字

- 修饰变量：表常量（命名规范--所有字母大写），不能被更改

- 修饰方法：最终方法，不能被重写

- 修饰类:  最终类，不能被继承

- 注意：1.修饰引用数据类型变量***是地址值不可更改，但是内部的属性值可以（比如通过set方法）***

  2.修饰基本数据类型其值不能更改

### 5.抽象方法（关键字-abstract）

* 抽象方法必须放到抽象类（特殊父类）
* 子类强制重写
* 抽象类不允许实例化，可以没有抽象方法

### 6.接口（关键字-interface）

- 抽象方法（声明规则），接口改写

- 格式： 

  ```java
  public interface 接口名{}//没括号
  ```

  

- 接口不能实例化

- 接口和类是实现关系, 通过implements关键字表示

  ```java
  public class 接口实现类类名 implements 接口名{} //接口的实现类(可以看成子类,包括继承力量)
  ```

- 接口实现类命名规范----接口名+Impl
- 接口实现类重写接口抽象方法
- ***接口实现类可以实现多个接口***
- ***接口成员变量只能是常量,默认public,static和 final修饰***
- 接口没有构造方法, 接口实现类的构造方法中super访问object
- **接口成员方法默认是抽象方法 系统默认用public 和 abstract修饰**
- 如果子类继承父类的方法有接口的方法了,就不用重写
- ***接口之间可以继承***

### 7.多态

前提：继承和实现关系，有方法重写，有父类引用指向子类对象

- 多态创建对象，调用成员变量时访问的是父类的成员变量

- ***成员变量：编译看左边（父类），运行看左边（父类）***-----走父类

- ***成员方法：编译看左边（父类），运行看右边（子类）***-----走子类

  **多态好处：**定义方法时，父类作为参数，方法就可以接受父类的任意子类对象

  **多态弊端：***方法不能调用子类特有方法*

  - ***转型（向上（子到父）和向下（父到子））***

  - 向下转型要用强制转换
  
  ```java
  Zi zi =(Zi) fu
  ```
  
  然后就可以使用子类特有方法, 但是这样其他子类就会存在转型隐患, 我们可以使用如下判断进行完善
  
  ```java
  if(a instanceof Zi){}
  ```
  

# 理解

- 继承和接口的区别：

  继承：
  体现类与类之间的“is-a”关系。
  子类继承父类的属性和方法，实现**代码复用。**
  单继承限制，一个类只能有一个直接父类。

  接口：
  体现类与接口之间的“has-a”关系。
  类实现接口时需要实现接口中定义的所有方法，实现多态性。
  一个类可以实现多个接口，提供了更大的灵活性。

- 基本数据类型和引用数据类型的区别

  基本数据类型：直接存储数据值，按值传递，有默认值，使用==比较值。
  引用数据类型：存储对象的引用，按引用传递，默认值是null，使用equals()比较内容。
