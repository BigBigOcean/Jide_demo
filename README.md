# Just some notes
for learning JAVA

length——数组的属性；
length()——String的方法；
size()——集合的方法

为了更好地组织类，Java 提供了包机制，用于区别类名的命名空间。
包的作用：
1、把功能相似或相关的类或接口组织在同一个包中，方便类的查找和使用。
2、如同文件夹一样，包也采用了树形目录的存储方式。同一个包中的类名字是不同的，不同的包中的类的名字是可以相同的，当同时调用两个不同包中相同类名的类时，应该加上包名加以区别。因此，包可以避免名字冲突。
3、包也限定了访问权限，拥有包访问权限的类才能访问某个包中的类。
Java 使用包（package）这种机制是为了防止命名冲突，访问控制，提供搜索和定位类（class）、接口、枚举（enumerations）和注释（annotation）等。

以下表达式的类型和值是什么？（注意整数除法）（-6.0）
-5 + 1/4 + 2*-3 + 5.0
因为int 类型   1/4 = 0

linux中tar部分命令参数
-s 还原文件的顺序和备份文件内的存放顺序相同。
-t 列出备份文件的内容。
-v 显示指令执行过程。
-f 指定压缩文件
-x 从备份文件中还原文件。

字符串常量池就是用来存储字符串的。它存在于Java 堆内存。

为什么我们在使用HashMap的时候总是用String做key？
因为字符串是不可变的，当创建字符串时，它的它的hashcode被缓存下来，不需要再次计算。因为HashMap内部实现是通过key的hashcode来确定value的存储位置，所以相比于其他对象更快。这也是为什么我们平时都使用String作为HashMap对象。

String s1 = "abc";
StringBuffer s2 = new StringBuffer(s1);
System.out.println(s1.equals(s2));
输出false，因为s2不是String类型，String的equals方法进行了类型判断。

4、下面的代码将创建几个字符串对象。
String s1 = new String("Hello");  
String s2 = new String("Hello");
答案是3个对象.

第一，行1 字符串池中的“hello”对象。
第二，行1，在堆内存中带有值“hello”的新字符串。
第三，行2，在堆内存中带有“hello”的新字符串。这里“hello”字符串池中的字符串被重用。

JVM和垃圾回收：
当对象的所有引用都消失后，对象使用的内存将自动回收:
https://blog.csdn.net/dadiyang/article/details/82823447

JVM内存：
https://www.nowcoder.com/test/question/done?tid=25263884&qid=14817

-XX:-UseConcMarkSweepGC: 对老年代使用CMS收集器
-XX:-UseParallelGC: 对新生代使用 Parallel GC
-XX:-UseParallelOldGC: 在老年代和新生代都使用 Parallel GC
-XX:-HeapDumpOnOutOfMemoryError: 当应用发生OOM时创建一个线程转储（dump）。对诊断非常有用。
-XX:-PrintGCDetails: 打印GC的详细日志
-Xms512m: 设置初始堆大小为 512m
-Xmx1024m: 设置最大堆大小为 1024m
-XX:NewSize 和 -XX:MaxNewSize: 指定新生代的默认和最大空间。
-XX:NewRatio=3: 设置新生代和老年代大小的比例为 1:3
-XX:SurvivorRatio=10: 设置 Eden space 和 Survivor space 的比例

java Queue中 add/offer，element/peek，remove/poll中的三个方法均为重复的方法，在选择使用时不免有所疑惑，这里简单区别一下：
1、add()和offer()区别:
add()和offer()都是向队列中添加一个元素。一些队列有大小限制，因此如果想在一个满的队列中加入一个新项，调用 add() 方法就会抛出一个 unchecked 异常，而调用 offer() 方法会返回 false。因此就可以在程序中进行有效的判断！
2、poll()和remove()区别：
remove() 和 poll() 方法都是从队列中删除第一个元素。如果队列元素为空，调用remove() 的行为与 Collection 接口的版本相似会抛出异常，但是新的 poll() 方法在用空集合调用时只是返回 null。因此新的方法更适合容易出现异常条件的情况。
3、element() 和 peek() 区别：
element() 和 peek() 用于在队列的头部查询元素。与 remove() 方法类似，在队列为空时， element() 抛出一个异常，而 peek() 返回 null。
下面是Java中Queue的一些常用方法：
add         增加一个元索                      如果队列已满，则抛出一个IIIegaISlabEepeplian异常
remove   移除并返回队列头部的元素     如果队列为空，则抛出一个NoSuchElementException异常
element  返回队列头部的元素              如果队列为空，则抛出一个NoSuchElementException异常
offer       添加一个元素并返回true        如果队列已满，则返回false
poll         移除并返问队列头部的元素     如果队列为空，则返回null
peek       返回队列头部的元素              如果队列为空，则返回null
put         添加一个元素                       如果队列满，则阻塞

抽象方法不能有方法体，只能申明

接口中的属性在不提供修饰符修饰的情况下，会自动加上public static final

flush（）函数强制将缓冲区中的字符流、字节流等输出，目的是如果输出流输出到缓冲区完成后，缓冲区并没有填满，那么缓冲区将会一直等待被填满。所以在关闭输出流之前要调用flush（）。

没有被public，protected，private修饰的类成员，只有同一个包里的类中可以访问，其余都不行

插入排序：最佳O（N）
快速排序：最佳O（NlogN）
堆 排 序：最佳O（NlogN）
归并排序：最佳O（NlogN）

大多数 JVM 将内存区域划分为
Method Area（Non-Heap）（方法区） ,
Heap（堆） , 
Program Counter Register（程序计数器） ,  
VM Stack（虚拟机栈，也有翻译成JAVA 方法栈的）,
Native Method Stack  （ 本地方法栈 ），
其中Method Area 和  Heap 是线程共享的  ，
VM Stack，Native Method Stack  和Program Counter Register  是非线程共享的。

概括地说来，JVM初始运行的时候都会分配好 Method Area（方法区） 和Heap（堆） ，
而JVM 每遇到一个线程，就为其分配一个 Program Counter Register（程序计数器） ,  VM Stack（虚拟机栈）和Native Method Stack  （本地方法栈）， 
当线程终止时，三者（虚拟机栈，本地方法栈和程序计数器）所占用的内存空间也会被释放掉。
这也是为什么我把内存区域分为线程共享和非线程共享的原因，非线程共享的那三个区域的生命周期与所属线程相同，而线程共享的区域与JAVA程序运行的生命周期相同，所以这也是系统垃圾回收的场所只发生在线程共享的区域（实际上对大部分虚拟机来说知发生在Heap上）的原因。

征程
1.Statement、PreparedStatement和CallableStatement都是接口(interface)。  
2.Statement继承自Wrapper、PreparedStatement继承自Statement、CallableStatement继承自PreparedStatement。  
3.  
Statement接口提供了执行语句和获取结果的基本方法；  
PreparedStatement接口添加了处理 IN 参数的方法；  
CallableStatement接口添加了处理 OUT 参数的方法。  
4.  
a.Statement:  
普通的不带参的查询SQL；支持批量更新,批量删除;  
b.PreparedStatement:  
可变参数的SQL,编译一次,执行多次,效率高;  
安全性好，有效防止Sql注入等问题;  
支持批量更新,批量删除;  
c.CallableStatement:  
继承自PreparedStatement,支持带参数的SQL操作;  
支持调用存储过程,提供了对输出和输入/输出参数(INOUT)的支持;  

Statement每次执行sql语句，数据库都要执行sql语句的编译 ，  
最好用于仅执行一次查询并返回结果的情形，效率高于PreparedStatement。  

PreparedStatement是预编译的，使用PreparedStatement有几个好处  
1. 在执行可变参数的一条SQL时，PreparedStatement比Statement的效率高，因为DBMS预编译一条SQL当然会比多次编译一条SQL的效率要高。  
2. 安全性好，有效防止Sql注入等问题。  
3.  对于多次重复执行的语句，使用PreparedStament效率会更高一点，并且在这种情况下也比较适合使用batch；  
4.  代码的可读性和可维护性。

java 转型问题其实并不复杂，只要记住一句话：父类引用指向子类对象。子类引用不能指向父类对象。
向上转型：
https://blog.csdn.net/u013457570/article/details/51311871
对比：
https://blog.csdn.net/eqiang8271/article/details/20717613
情况分类：
https://blog.csdn.net/u013457570/article/details/51311871

FileOutputStream 是字节流，它一个字节一个字节的向外边送数据
OutputStreamWrite是字符流，它一个字符一个字符的向外边送数据
它们有什么区别么？
解析：
      因为计算机是洋鬼子发明的，它们的英文字符占一个字节，而我们的中文是一个字符，占俩字节。
     如果用stream，你读出来的英语再倒也罢了，读出来的中文可就是乱码或者一个个“？？？？”。
     如果你用WRITER，就不会有乱码了，明白？
BufferedWriter  Buffer是一个缓冲区，为什么要用BUFFER呢？
    如果你直接用stream或者writer，你的硬盘可能就是一个字符或者一个字节    读写硬盘一次，
可是你用了Buffer，你的硬盘就是读了一堆数据之后，读写一下硬盘。这样对你硬盘有好处。

关于finally执行：
https://blog.csdn.net/Dove_Knowledge/article/details/71077512
1.执行try里面的return也会执行finally里面的语句
2.finally里面的return会覆盖前面的return
3.如果碰到system的exit语句或者在进入try之前就发生了语法错误中断程序，则finally不会执行

尽量不要做字符转化，因为UTF8转GBK再转回UTF8会造成乱码

Java的正则表达式：
pattern代表一个正则词，march是判断匹配；
match的判断方法可以有matches和lookingAt，前者是全匹配，后者是包含匹配
*表示*前面的字符可以有零个或者多个

为什么main方法是静态的（static）

正因为main方法是静态的，JVM调用这个方法就不需要创建任何包含这个main方法的实例。
因为C和C++同样有类似的main方法作为程序执行的入口。
如果main方法不声明为静态的，JVM就必须创建main类的实例，因为构造器可以被重载，JVM就没法确定调用哪个main方法。
静态方法和静态数据加载到内存就可以直接调用而不需要像实例方法一样创建实例后才能调用，如果main方法是静态的，那么它就会被加载到JVM上下文中成为可执行的方法。

为什么main方法是公有的（public）
Java指定了一些可访问的修饰符如：private、protected、public，任何方法或变量都可以声明为public，Java可以从该类之外的地方访问。因为main方法是公共的，JVM就可以轻松的访问执行它。

为什么main方法没有返回值（Void） 
因为main返回任何值对程序都没任何意义，所以设计成void，意味着main不会有任何值返回

JAVA动态数组：
ArrayList List = new ArrayList(); 
for( int i=0;i <10;i++ ) //给数组增加10个Int元素 
List.Add(i); 
//..程序做一些处理 
List.RemoveAt(5);//将第6个元素移除 
for( int i=0;i <3;i++ ) //再增加3个元素 
List.Add(i+20); 
Int32[] values = (Int32[])List.ToArray(typeof(Int32));//返回ArrayList包含的数组

