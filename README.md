# InterviewQuation
 ## 安卓面试的一些问题  
 
**java基础部分**
 
1. **java中==和equals和hashCode的区别**
        1)基本数据类型，也称原始数据类型byte,short,char,int,long,float,double,boolean   他们之间的比较，应用双等号（==）,比较的是他们的值。  
		2) 引用类型(类、接口、数组)   当他们用（==）进行比较的时候，比较的是他们在内存中的存放地址，
		所以，除非是同一个new出来的对象，他们的比较后的结果为true，否则比较后结果为false。
		对象是放在堆中的，栈中存放的是对象的引用（地址）。由此可见'=='是对栈中的值进行比较的。
		如果要比较堆中对象的内容是否相同，那么就要重写equals方法了。  
        3)默认情况（没有覆盖equals方法）下equals方法都是调用Object类的equals方法，
		而Object的equals方法主要用于判断对象的内存地址引用是不是同一个地址（是不是同一个对象）  
        4)要是类中覆盖了equals方法，那么就要根据具体的代码来确定equals方法的作用了，覆盖后一般都是通过对象的内容是否相等来判断对象是否相等。  
        5)hashCode()方法返回的就是一个数值，从方法的名称上就可以看出，其目的是生成一个hash码。hash码的主要用途就是在对对象进行散列的时候作为key输入，
		据此很容易推断出，我们需要每个对象的hash码尽可能不同，这样才能保证散列的存取性能。事实上，Object类提供的默认实现确实保证每个对象的hash码不同
		（在对象的内存地址基础上经过特定算法返回一个hash码）。Java采用了哈希表的原理。哈希（Hash）实际上是个人名，由于他提出一哈希算法的概念，
		所以就以他的名字命名了。 哈希算法也称为散列算法，是将数据依特定算法直接指定到一个地址上  
		
        - 如果两个对象equals，Java运行时环境会认为他们的hashcode一定相等。  
		- 如果两个对象不equals，他们的hashcode有可能相等。  
		- 如果两个对象hashcode相等，他们不一定equals。  
		- 如果两个对象hashcode不相等，他们一定不equals。 		
         2.引用类型(类、接口、数组)   
         当他们用（==）进行比较的时候，比较的是他们在内存中的存放地址，所以，除非是同一个new出来的对象，他们的比较后的结果为true，否则比较后结果为false。对象是放在堆中的，栈中存放的是对象的引用（地址）。由此可见'=='是对栈中的值进行比较的。如果要比较堆中对象的内容是否相同，那么就要重写equals方法了。 

2. **int、char、long各占多少字节数**  
    byte是1字节，char是2字节，int是4字节，float是4字节，long是8字节，同时double是8字节，boolean至少是1字节  
	

3. **int与integer的区别**  
    *1)值的存储*  
	int 存储在栈中
    *2)Integer 对象的引用存储在栈空间中，对象的数据存储在堆空间中。*  
	初始化:int 初始化值为0。Integer 初始化值为null。  
	*3)传参*  
	int 是值传递，栈中的数据不可变。  
	Integer 对象是引用传递，引用不可变，但是引用指向的堆空间地址中的值是可以改变的。  
	*4)泛型支持*  
	泛型不支持int，但是支持Integer。
    *5)运算*  
	int 可以直接做运算，是类的特性。  
	Integer 的对象可以调用该类的方法，但是在拆箱之前不能进行运算，需要转化为基本类型int



4. **谈谈对java多态的理解**
    面向对象编程有三个特征，即封装、继承和多态。继承是为了重用父类代码，同时为实现多态性作准备。  
 

5. String、StringBuffer、StringBuilder区别



6. 什么是内部类？内部类的作用



7. 抽象类和接口区别



8. 抽象类的意义


9. 抽象类与接口的应用场景

10. 抽象类是否可以没有方法和属性

11. 接口的意义

12. 泛型中extends和super的区别

13. 父类的静态方法能否被子类重写

14. 进程和线程的区别

15. final，finally，finalize的区别

16. 序列化的方式

17. Serializable 和Parcelable 的区别

18. 静态属性和静态方法是否可以被继承？是否可以被重写？以及原因？

19. 静态内部类的设计意图

20. 成员内部类、静态内部类、局部内部类和匿名内部类的理解，以及项目中的应用

21. 谈谈对kotlin的理解

22. 闭包和局部内部类的区别

23. string 转换成 integer的方式及原理