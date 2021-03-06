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
 

5. **String、StringBuffer、StringBuilder区别**  
   String是字符串常量，常量是不可以被修改的，所以String对象一旦被创建是不能改变的，其执行速度是最慢的，但是不可变也注定其线程是安全的  
   StringBulider和StringBuffer的对象是变量，对变量进行操作就是直接改变变量的值，而不进行创建回收，所以速度要比String快的多。  
   StringBuffer：线程安全的可以被多个线程安全使用，其方法大都采用了 synchronized 关键字进行修饰，因此是线程安全的  
   StringBuilder：线程不安全的，而 StringBuilder 没有这个修饰，可以被认为是线程不安全的。 因此其速度也是最快的   
   

6. **什么是内部类？内部类的作用**  
    一个类定义到另外一个类的内部，在类里面的这个类就叫内部类，外面的类就叫外部类。  
	*1)隐藏你不想让别人知道的操作，也即封装性。*  
	*2)一个内部类对象可以访问创建它的外部类对象的内容，甚至包括私有变量！*
	*3)内部类可以分为多种；主要以下4种:静态内部类，成员内部类，局部内部类，匿名内部类
- 静态内部类:静态内部类是指被声明为static的内部类，他可以不依赖内部类而实例，而通常的内部类需要实例化外部类，从而实例化。静态内部类不可以有与外部类有相同的类名。不能访问外部类的普通成员变量，但是可以访问静态成员变量和静态方法（包括私有类型）
- 成员内部类:一个 静态内部类去掉static 就是成员内部类，他可以自由的引用外部类的属性和方法，无论是静态还是非静态。但是不可以有静态属性和方法
- 局部内部类:定义在一个代码块的内类,他的作用范围是所在代码块，是内部类中最少使用的一类型。局部内部类跟局部变量一样，不能被public ，protected，private以及static修饰，只能访问方法中定义final类型的局部变量  
- 匿名内部类:匿名内部类是一种没有类名的内部类，不使用class，extends，implements，没有构造函数，他必须继承其他类或实现其他接口。匿名内部类的好处是使代码更加简洁，紧凑，但是带来的问题是易读性下降。  


7. **抽象类和接口区别**  
- 抽象类是用来捕捉子类的通用性的，它不能被实例化，只能用作子类的超类，抽象类是被用来创建继承层级里子类的模板  
- 接口是抽象方法的集合，如果一个类实现了某个接口，那么它就继承了这个接口的抽象方法，就像契约模式，如果实现了这个接口，
那么就必须保证使用这些方法，并且实现这些方法，接口是一种形式，接口自身不能做任何事情，接口里面的方法默认都是abstract的  
- 抽象类是对一种事务的抽象，是对整个类进行抽象，包括属性，行为（方法）。接口是对行为（行为）的抽象。如果一个类继承或实现了某个抽象类，
那么一定是抽象类的种类（拥有同一种属性或行为的类）  
- 设计层面不同，抽象类作为很多子类的父类，是一种模板设计，而接口是一种规范，它是一种辐射式设计，也就是说对于抽象类，
如果需要添加新的方法，可以直接在抽象方法中添加实现，子类可以不用变更


8. **抽象类的意义**  
- 因为抽象类不能实例化对象，所以必须要有子类来实现它之后才能使用。这样就可以把一些具有相同属性和方法的组件进行抽象，这样更有利于代码和程序的维护。  
- 当又有一个具有相似的组件产生时，只需要实现该抽象类就可以获得该抽象类的那些属性和方法。


9. **抽象类与接口的应用场景**  
   ##### 抽象类  
- 在某些情况下，某个父类只是知道其子类应该包含怎样的方法，但无法准确知道这些子类如何实现这些方法。  
- 从多个具有相同特征的类中抽象出一个抽象类，以这个抽象类作为子类的模板，从而避免了子类设计的随意性。  
   ##### 接口  
- 一般情况下，实现类和它的抽象类之前具有 "is-a" 的关系，但是如果我们想达到同样的目的，但是又不存在这种关系时，使用接口。  
- 由于 java 中单继承的特性，导致一个类只能继承一个类，但是可以实现一个或多个接口，此时可以使用接口。   


10. **抽象类是否可以没有方法和属性**  
- 抽象类专用于派生出子类，子类必须实现抽象类所声明的抽象方法，否则，子类仍是抽象类。 包含抽象方法的类一定是抽象类，但抽象类中的方法不一定是抽象方法。  
- 抽象类中可以没有抽象方法，但有抽象方法的一定是抽象类（如HttpServlet）。但即使抽象类中没有抽象方法，也不能被new出来。  
- 没有抽象类方法的抽象类的存在价值在于：类已经定义好了，不能改变其中的方法体（实例化出来的对象满足不了要求），只有继承并重写了他的子类才能满足要求，
所以才把它定义为没有抽象方法的抽象类。


11. **接口的意义**  
- 定义接口有利于代码的规范
- 有利于对代码进行维护
- 保证代码的安全和严密


12. **泛型中extends和super的区别 ** 



13. **父类的静态方法能否被子类重写**  
*父类的静态方法可以被子类继承，但是不能重写*

 
14. **进程和线程的区别**  
- 进程是具有一定独立功能的程序关于某个数据集合上的一次运行活动,进程是系统进行资源分配和调度的一个独立单位  
- 线程是进程的一个实体,是CPU调度和分派的基本单位,它是比进程更小的能独立运行的基本单位.线程自己基本上不拥有系统资源,只拥有一点在运行中必不可少的资源(如程序计数器,一组寄存器和栈),但是它可与同属一个进程的其他的线程共享进程所拥有的全部资源  
- 一个线程可以创建和撤销另一个线程;同一个进程中的多个线程之间可以并发执行  
- 相对进程而言，线程是一个更加接近于执行体的概念，它可以与同进程中的其他线程共享数据，但拥有自己的栈空间，拥有独立的执行序列  
- 进程有独立的地址空间，一个进程崩溃后，在保护模式下不会对其它进程产生影响，而线程只是一个进程中的不同执行路径  
- 线程有自己的堆栈和局部变量，但线程之间没有单独的地址空间，一个线程死掉就等于整个进程死掉，所以多进程的程序要比多线程的程序健壮，但在进程切换时，耗费资源较大，效率要差一些  
  **总结如下  
          1) 简而言之,一个程序至少有一个进程,一个进程至少有一个线程.  		  
		  2) 线程的划分尺度小于进程，使得多线程程序的并发性高。  
		  3) 另外，进程在执行过程中拥有独立的内存单元，而多个线程共享内存，从而极大地提高了程序的运行效率。  
		  4) 线程在执行过程中与进程还是有区别的。每个独立的线程有一个程序运行的入口、顺序执行序列和程序的出口。但是线程不能够独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。  
		  5) 从逻辑角度来看，多线程的意义在于一个应用程序中，有多个执行部分可以同时执行。但操作系统并没有将多个线程看做多个独立的应用，来实现进程的调度和管理以及资源分配。这就是进程和线程的重要区别  
		  
		  
15. **final，finally，finalize的区别**  
- 当final修饰一个基本数据类型时，表示该基本数据类型的值一旦在初始化后便不能发生变化；如果final修饰一个引用类型时，则在对其初始化之后便不能再让其指向其他对象了，
但该引用所指向的对象的内容是可以发生变化的。本质上是一回事，因为引用的值是一个地址，final要求值，即地址的值不发生变化。final修饰一个成员变量（属性），
必须要显示初始化。这里有两种初始化方式，一种是在变量声明的时候初始化；第二种方法是在声明变量的时候不赋初值，但是要在这个变量所在的类的所有的构造函数中对这个变量赋初值  
- finally作为异常处理的一部分，它只能用在try/catch语句中，并且附带一个语句块，表示这段语句最终一定会被执行（不管有没有抛出异常），经常被用在需要释放资源的情况下  
- finalize()是在java.lang.Object里定义的，也就是说每一个对象都有这么个方法。这个方法在gc启动，该对象被回收的时候被调用。其实gc可以回收大部分的对象（凡是new出来的对象，gc都能搞定，一般情况下我们又不会用new以外的方式去创建对象），所以一般是不需要程序员去实现finalize的。 
特殊情况下，需要程序员实现finalize，当对象被回收的时候释放一些资源，比如：一个socket链接，在对象初始化时创建，整个生命周期内有效，那么就需要实现finalize，关闭这个链接。 使用finalize还需要注意一个事，调用super.finalize();
一个对象的finalize()方法只会被调用一次，而且finalize()被调用不意味着gc会立即回收该对象，所以有可能调用finalize()后，该对象又不需要被回收了，然后到了真正要被回收的时候，因为前面调用过一次，所以不会调用finalize()，产生问题。 所以，推荐不要使用finalize()方法，它跟析构函数不一样。  
 

16. **序列化的方式**  
- 是相应的对象实现了序列化接口Serializable，这个使用的比较多，对于序列化接口Serializable接口是一个空的接口，它的主要作用就是标识这个对象时可序列化的，jre对象在传输对象的时候会进行相关的封装  
- Parcelable 接口(不仅仅需要声明,还需要实现内部的相应方法)


17. **Serializable 和Parcelable 的区别**  
- 作用：Serializable的作用是为了保存对象的属性到本地文件、数据库、网络流、rmi以方便数据传输，当然这种传输可以是程序内的也可以是两个程序间的。而Android的  
Parcelable的设计初衷是因为Serializable效率过慢，为了在程序内不同组件间以及不同Android程序间(AIDL)高效的传输数据而设计，这些数据仅在内存中存在，Parcelable是通过IBinder通信的消息的载体。  
- 效率及选择： Parcelable的性能比Serializable好，在内存开销方面较小，所以在内存间数据传输时推荐使用Parcelable，如activity间传输数据，而Serializable可将数据持久化方便
保存，所以在需要保存或网络传输数据时选择Serializable，因为android不同版本Parcelable可能不同，所以不推荐使用Parcelable进行数据持久化。  
- 编程实现：对于Serializable，类只需要实现Serializable接口，并提供一个序列化版本id(serialVersionUID)即可。而Parcelable则需要实现writeToParcel、
describeContents函数以及静态的CREATOR变量，实际上就是将如何打包和解包的工作自己来定义，而序列化的这些操作完全由底层实现。  


18. **静态属性和静态方法是否可以被继承？是否可以被重写？以及原因？**  
- java中静态属性和静态方法可以被继承，但是没有被重写(overwrite)而是被隐藏.
- 原因：1). 静态方法和属性是属于类的，调用的时候直接通过类名.方法名完成对，不需要继承机制及可以调用。如果子类里面定义了静态方法和属性，那么这时候父类的静态方法或属性称之为"隐藏"。如果你想要调用父类的静态方法和属性，直接通过父类名.方法或变量名完成，至于是否继承一说，子类是有继承静态方法和属性，但是跟实例方法和属性不太一样，存在"隐藏"的这种情况。  
		2). 多态之所以能够实现依赖于继承、接口和重写、重载（继承和重写最为关键）。有了继承和重写就可以实现父类的引用指向不同子类的对象。重写的功能是："重写"后子类的优先级要高于父类的优先级，但是“隐藏”是没有这个优先级之分的。  
		3). 静态属性、静态方法和非静态的属性都可以被继承和隐藏而不能被重写，因此不能实现多态，不能实现父类的引用可以指向不同子类的对象。非静态方法可以被继承和重写，因此可以实现多态。
		
   
19. **静态内部类的设计意图**  
- 非静态内部类在编译完成之后会隐含地保存着一个引用，该引用是指向创建它的外围内，但是静态内部类却没有。每个内部类都能独立地继承一个（接口的）实现，
所以无论外围类是否已经继承了某个（接口的）实现，对于内部类都没有影响。在我们程序设计中有时候会存在一些使用接口很难解决的问题，这个时候我们可以利用内部类提供的、
可以继承多个具体的或者抽象的类的能力来解决这些程序设计问题。可以这样说，接口只是解决了部分问题，而内部类使得多重继承的解决方案变得更加完整。


20. **成员内部类、静态内部类、局部内部类和匿名内部类的理解，以及项目中的应用**  
- 成员内部类：定义在类内部的非静态类，就是成员内部类。  
- 静态内部类：定义在类内部的静态类，就是静态内部类。 *使用场景* ：Java集合类HashMap内部就有一个静态内部类Entry。Entry是HashMap存放元素的抽象，HashMap内部维护Entry数组用了存放元素，
但是Entry对使用者是透明的。像这种和外部类关系密切的，且不依赖外部类实例的，都可以使用静态内部类。  
- 局部内部类： 定义在方法中的类，就是局部类。 *应用场景* ：如果一个类只在某个方法中使用，则可以考虑使用局部类。  
- 匿名内部类：匿名内部类是没有访问修饰符的。 *应用场景* ：匿名内部类使用广泛，比如我们常用的绑定监听的时候


21. 谈谈对kotlin的理解  


22. 闭包和局部内部类的区别  


23. string 转换成 integer的方式及原理


## Android多线程  
1. **什么是线程**  
     线程就是进程中运行的多个子任务，是操作系统调用的最小单元  


2. **线程的状态**  
- New:新建状态，new出来，还没有调用start  
- Runnable:可运行状态，调用start进入可运行状态，可能运行也可能没有运行，取决于操作系统的调度  
- Blocked:阻塞状态，被锁阻塞，暂时不活动，阻塞状态是线程阻塞在进入  
- synchronized:关键字修饰的方法或代码块(获取锁)时的状态。  
- Waiting:等待状态，不活动，不运行任何代码，等待线程调度器调度，wait、sleep用来暂停当前线程的执行，以毫秒为单位，任何其它线程都可以中断当前线程的睡眠，这种情况下将抛出InterruptedException异常  
- Timed Waiting:超时等待，在指定时间自行返回  
- 终止状态，包括正常终止和异常终止  


3. **线程的创建**  
- 继承Thread重写run方法  
- 实现Runnable重写run方法  
- 实现Callable重写call方法  
(实现Callable重写call方法
实现Callable和实现Runnable类似，但是功能更强大，具体表现在

a.可以在任务结束后提供一个返回值，Runnable不行

b.call方法可以抛出异常，Runnable的run方法不行

c.可以通过运行Callable得到的Fulture对象监听目标线程调用call方法的结果，得到返回值，（fulture.get(),调用后会阻塞，直到获取到返回值）  
(实现Callable重写call方法:a.可以在任务结束后提供一个返回值，Runnable不行   b.call方法可以抛出异常，Runnable的run方法不行  c.可以通过运行Callable得到的Fulture对象监听目标线程调用call方法的结果，得到返回值，fulture.get(),调用后会阻塞，直到获取到返回值)


4. **Thread为什么不能用stop方法停止线程**  
- 从SUN的官方文档可以得知，调用Thread.stop()方法是不安全的，这是因为当调用Thread.stop()方法时，会发生下面两件事：  
    1) 即刻抛出 ThreadDeath异常，在线程的run()方法内，任何一点都有可能抛出ThreadDeath Error，包括在catch或finally语句中。 	 
    2) 释放该线程所持有的所有的锁。调用thread.stop()后导致了该线程所持有的所有锁的突然释放，那么被保护数据就有可能呈现不一致性，其他线程在使用这些被破坏的数据时，有可能导致一些很奇怪的应用程序错误  
	
	
5. **同步方法和同步代码块**  
- 同步方法:即有synchronized关键字修饰的方法, 由于java的每个对象都有一个内置锁，当用此关键字修饰方法时，内置锁会保护整个方法。在调用该方法前，需要获得内置锁，否则就处于阻塞状态  
- 同步代码块：即有synchronized关键字修饰的语句块,被该关键字修饰的语句块会自动被加上内置锁，从而实现同步  
- 使用特殊域变量(volatile)实现线程同步：a.volatile关键字为域变量的访问提供了一种免锁机制     注：多线程中的非同步问题主要出现在对域的读写上，如果让域自身避免这个问题，则就不需要修改操作该域的方法。用final域，有锁保护的域和volatile域可以避免非同步的问题。  
- 使用重入锁实现线程同步: 在JavaSE5.0中新增了一个java.util.concurrent包来支持同步。ReentrantLock类是可重入、互斥、实现了Lock接口的锁， 它与使用synchronized方法和快具有相同的基本行为和语义，并且扩展了其能力  
- 使用局部变量实现线程同步:如果使用ThreadLocal管理变量，则每一个使用该变量的线程都获得该变量的副本， 副本之间相互独立，这样每一个线程都可以随意修改自己的变量副本，而不会对其他线程产生影响  


6. **volatile关键字**  
    volatile为实例域的同步访问提供了免锁机制，如果声明一个域为volatile，那么编译器和虚拟机就直到该域可能被另一个线程并发更新  
	

7. **原子性 可见性 有序性**  
- 原子性：对基本数据类型的读取和赋值操作是原子性操作，这些操作不可被中断，是一步到位的，例如x=3是原子性操作，而y = x就不是，它包含两步：第一读取x，第二将x写入工作内存；x++也不是原子性操作，它包含三部，第一，读取x，第二，对x加1，第三，写入内存。原子性操作的类如：AtomicInteger AtomicBoolean AtomicLong AtomicReference  
- 可见性：指线程之间的可见性，既一个线程修改的状态对另一个线程是可见的。volatile修饰可以保证可见性，它会保证修改的值会立即被更新到主存，所以对其他线程是可见的，普通的共享变量不能保证可见性，因为被修改后不会立即写入主存，何时被写入主存是不确定的，所以其他线程去读取的时候可能读到的还是旧值  
- 有序性：Java中的指令重排序（包括编译器重排序和运行期重排序）可以起到优化代码的作用，但是在多线程中会影响到并发执行的正确性，使用volatile可以保证有序性，禁止指令重排volatile可以保证可见性 有序性，但是无法保证原子性，在某些情况下可以提供优于锁的性能和伸缩性，替代sychronized关键字简化代码，但是要严格遵循使用条件  


8. **线程池ThreadPoolExecutor**  
线程池的工作原理：线程池可以减少创建和销毁线程的次数，从而减少系统资源的消耗，当一个任务提交到线程池时  
a. 首先判断核心线程池中的线程是否已经满了，如果没满，则创建一个核心线程执行任务，否则进入下一步  
b. 判断工作队列是否已满，没有满则加入工作队列，否则执行下一步  
c. 判断线程数是否达到了最大值，如果不是，则创建非核心线程执行任务，否则执行饱和策略，默认抛出异常  

9. **线程池的种类**  
- FixedThreadPool:可重用固定线程数的线程池，只有核心线程，没有非核心线程，核心线程不会被回收，有任务时，有空闲的核心线程就用核心线程执行，没有则加入队列排队  
- SingleThreadExecutor:单线程线程池，只有一个核心线程，没有非核心线程，当任务到达时，如果没有运行线程，则创建一个线程执行，如果正在运行则加入队列等待，可以保证所有任务在一个线程中按照顺序执行，和FixedThreadPool的区别只有数量  
- CachedThreadPool:按需创建的线程池，没有核心线程，非核心线程有Integer.MAX_VALUE个，每次提交  
- ScheduledThreadPoolExecutor:继承自ThreadPoolExecutor,用于延时执行任务或定期执行任务，核心线程数固定，线程总数为Integer.MAX_VALUE  


10. **线程同步机制与原理，举例说明**  
为什么需要线程同步？当多个线程操作同一个变量的时候，存在这个变量何时对另一个线程可见的问题，也就是可见性。每一个线程都持有主存中变量的一个副本，当他更新这个变量时，
首先更新的是自己线程中副本的变量值，然后会将这个值更新到主存中，但是是否立即更新以及更新到主存的时机是不确定的，这就导致当另一个线程操作这个变量的时候，他从主存中读取的这个变量还是旧的值，
导致两个线程不同步的问题。线程同步就是为了保证多线程操作的可见性和原子性，比如我们用synchronized关键字包裹一端代码，我们希望这段代码执行完成后，对另一个线程立即可见，
另一个线程再次操作的时候得到的是上一个线程更新之后的内容，还有就是保证这段代码的原子性，这段代码可能涉及到了好几部操作，我们希望这好几步的操作一次完成不会被中间打断，
锁的同步机制就可以实现这一点。一般说的synchronized用来做多线程同步功能，其实synchronized只是提供多线程互斥，而对象的wait()和notify()方法才提供线程的同步功能。
JVM通过Monitor对象实现线程同步，当多个线程同时请求synchronized方法或块时，monitor会设置几个虚拟逻辑数据结构来管理这些多线程。
新请求的线程会首先被加入到线程排队队列中，线程阻塞，当某个拥有锁的线程unlock之后，则排队队列里的线程竞争上岗（synchronized是不公平竞争锁，下面还会讲到）。
如果运行的线程调用对象的wait()后就释放锁并进入wait线程集合那边，当调用对象的notify()或notifyall()后，wait线程就到排队那边。这是大致的逻辑。


11. **app的启动流程  
app启动的过程有两种情况，第一种是从桌面launcher上点击相应的应用图标，第二种是在activity中通过调用startActivity来启动一个新的activity。

我们创建一个新的项目，默认的根activity都是MainActivity，而所有的activity都是保存在堆栈中的，我们启动一个新的activity就会放在上一个activity上面，
而我们从桌面点击应用图标的时候，由于launcher本身也是一个应用，当我们点击图标的时候，系统就会调用startActivitySately(),一般情况下，
我们所启动的activity的相关信息都会保存在intent中，比如action，category等等。
我们在安装这个应用的时候，系统也会启动一个PackaManagerService的管理服务，这个管理服务会对AndroidManifest.xml文件进行解析，
从而得到应用程序中的相关信息，比如service，activity，Broadcast等等，然后获得相关组件的信息。当我们点击应用图标的时候，就会调用startActivitySately()方法，
而这个方法内部则是调用startActivty(),而startActivity()方法最终还是会调用startActivityForResult()这个方法。而在startActivityForResult()这个方法。
因为startActivityForResult()方法是有返回结果的，所以系统就直接给一个-1，就表示不需要结果返回了。而startActivityForResult()这个方法实际是通过Instrumentation
类中的execStartActivity()方法来启动activity，Instrumentation这个类主要作用就是监控程序和系统之间的交互。而在这个execStartActivity()方法中会获取
ActivityManagerService的代理对象，通过这个代理对象进行启动activity。启动会就会调用一个checkStartActivityResult()方法，如果说没有在配置清单中配置有这个组件，
就会在这个方法中抛出异常了。当然最后是调用的是Application.scheduleLaunchActivity()进行启动activity，而这个方法中通过获取得到一个ActivityClientRecord对象，
而这个ActivityClientRecord通过handler来进行消息的发送，系统内部会将每一个activity组件使用ActivityClientRecord对象来进行描述，
而ActivityClientRecord对象中保存有一个LoaderApk对象，通过这个对象调用handleLaunchActivity来启动activity组件，而页面的生命周期方法也就是在这个方法中进行调用。




