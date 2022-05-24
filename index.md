## Welcome to leifengrui Pages

I'm glad you found it here. If you want to contact me, I'll share my story here, leifengrui@outlook.com

# 牛客刷题

## 0524

### 1 HashSet子类依靠()方法区分重复元素。

HashSet内部使用**Map**保存数据，即将HashSet的数据作为Map的key值保存，这也是HashSet中元素不能重复的原因。而Map中保存key值前，会去判断当前Map中是否含有该key对象，内部是**先通过key的hashCode**，确定有相同的hashCode之后，再通过**equals**方法判断是否相同。

### 2 方法重载

如果两个方法只有返回值类型不同， 这两个方法在编译器看来还是同一个方法，

方法重载：方法名称相同，**参数列表不同**（可以是参数的类型，个数，顺序不同）

### 3 初始化过程

**初始化过程：**   **父类静态**代码块 ->**子类静态**代码块 ->父类**非静态代码块** -> 父类构造函数 -> 子类非静态代码块 -> 子类构造函数

初始化过程： 

1. 初始化父类中的静态成员变量和静态代码块 ； 
2. 初始化子类中的静态成员变量和静态代码块 ； 
3. 初始化父类的普通成员变量和代码块，再执行父类的构造方法；
4. 初始化子类的普通成员变量和代码块，再执行子类的构造方法； 



### 4 Thread.sleep() 和 Object.wait(),都可以抛出 InterruptedException。这个异常是不能忽略的

checked exception：指的是编译时异常，该类异常需要本函数必须处理的，用try和catch处理，或者用throws抛出异常，然后交给调用者去处理异常。

runtime exception：指的是运行时异常，该类异常不必须本函数必须处理，当然也可以处理。

### 5 string的参数问题

``` 
5 public class Example {  
  String str = new String("good");  
   char[] ch = {'a','b','c'};  
   public static void main(String[] args) {  
     Example ex = new Example();  
     ex.change(ex.str, ex.ch);  
     System.out.print(ex.str +"and");  
     System.out.print(ex.ch);   
  }  
  public void change(String str, char ch[]){  
     str= "test ok";  
     ch[0]= 'g';  
  }  
}		//goodandgbc
```

java 中String是 immutable的，也就是**不可变**，一旦初始化，其引用指向的内容是不可变的。

也就是说，String str = “aa”；str=“bb”；第二句不是改变“aa”所存储地址的内容，而是另外开辟了一个空间用来存储“bb”；同时由str指向

原来的“aa”，现在已经不可达，GC时会自动回收。

因此String作为参数传进来时候，str= "test ok"; 实际给副本引用str指向了新分配的地址，该地址存储“test ok”。

因此，**原先的str仍然指向“good”**

### 6 **substring** 

方法将返回一个包含从  *start*  到最后（不包含  *end*  ）的子字符串的字符串

简单来说 左闭右开

### 7 数组复制的最快方法

 复制的效率**System.arraycopy**>clone>Arrays.copyOf>for循环，这个有兴趣自己测试一下就知道了。这里面在System类源码中给出了**arraycopy的方法，是native方法**，也就是本地方法，肯定是最快的。而Arrays.copyOf(注意是Arrays类，不是Array)的实现，在源码中是调用System.copyOf的，多了一个步骤，肯定就不是最快的。

### 8能被java.exe成功运行的java class文件必须有main()方法

### 9 关于线程的运行 有些状态时没有办法互相到达的

![image-20220524210506896](C:\Users\lei\AppData\Roaming\Typora\typora-user-images\image-20220524210506896.png)

### 10 字符的大小

byte 1 8

short 2 16

int 4 32

long 8 64

float 4 32

double 8 64

char 2 16

boolean 1 8

### 11 instanceof

instance是java的二元运算符，用来判断他左边的对象是否为右面类（接口，抽象类，父类）的实例

### 12 yield 礼让

yiled方法属于高风亮节的行为，这个坑位我不上了，后面跟我同级别的先上厕所。这样比较好记！

高优先级的就是你们的县长，县长要上厕所，对不起，你得出来，县长先上，县长上完了，CPU分配到你了，你才能继续拉X。

因此 一个线程调用yield方法，可以使具有相同优先级线程获得处理器


苏ICP备2022019340号
