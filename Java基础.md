

### Java

------

##### 1、 Java历史

+ 学习知识点：语法结构 面向对象核心 工具类 集合 异常 线程 I/O 反射 注解

+ 历史背景：

  - Java创始人：1995诞生 James Gosling （詹姆斯 高斯林）

  - 背景故事：加拿大出生 计算机语言天才的高斯林，14岁记住大学计算机中心的密码，进入中心，自学编程，15岁作为分析卫星、天文数据的临时编程员，80年代初期获得博士学位，就业于IBM公司，工作组不被高层看好，跳槽SUN，Stanford University Network公司，注册公司SUN Microsystems。SUN公司成立了研发团队，试图预测未来软件技术发展趋势 James Gosling成为项目负责人。Green项目智能家居，存在不能跨平台的问题（各种不同规格的芯片），于是想开发一套内部使用的编程语言（沿用了C++语法结构），取名为橡树（Oak），摒弃了C++过于庞大，不能跨平台的缺点。1992年对Oak语言进行展示，硬件生产商不支持，因为新语言没有经过检验，而且需要重新学习新的语言特性，成本较高，所以Oak语言暂且被搁置。1995年Sun公司想参加硅谷全球性的IT盛会，因为Oak已经作为商标被注册了，所以将语言取名为Java。1995.5.23 Sun公司正式发布了Java语言；**1996.1 发布开发JDK1.0**；1997.2 JDK1.1版本问世；1998.12 JavaEE企业版发布；**1999.6 Java第二代平台**（Java2 Standard Edition桌面级），细化了三个不同的小版本（不同方向：Java2 Enterprise Edition企业级，Java2 Micro Edition移动端）

    ​	1）J2SE：Java2 Standard Edition 桌面级

    ​	2）J2EE：Java2 Enterprise Edition 企业级

    ​	3）J2ME：Java2 Micro Edition 移动端

    2004.5 **JDK1.5版本发布 很多新特性 Java5**

    2005.6 **Java6 最经典版本，留存最久的版本**

    2009由于公司运行不当，被全球第二大互联网公司Oracle并购（74亿$）

    2011 Oracle发布Java7版本

    2014 Oracle发布Java8

    2017 Oracle发布Java9

##### 2、Java火爆的原因

+ 跨平台性（最早是针对不同厂商的芯片，现在是支持不同版本的操作系统）
+ 面向对象
+ 简单性：省去了C++的多继承，指针等等
+ 健壮性：垃圾回收机制、异常处理机制等
+ 多线程：并行操作，提高了执行性能，线程安全问题
+ 大数据开发：Java与很多新的技术发展息息相关

##### 3、Java语言特点

+ 跨平台性：平台（操作系统）

  Java通过JVM（Java virtual machine ，Java虚拟机）来跨平台，根据不同得到操作系统下载不同的虚拟机就行

  虚拟机作用：在内存中开辟一块空间，会将Java源文件编译为字节码

  高级编程语言：计算机只认识0（不通电），1（通电），越贴近人类的编程语言越高级

  程序存储在哪里：程序就是英文，存储在一个地方，我们称之为文件

  执行程序的过程：写完的程序，计算机不认识，所以需要编译（将我们写好的源文件编译成计算机能识别的字节码文件），最终有两个文件，源文件和字节码文件（存在硬盘上）

+ 计算机的组成：硬件和软件

  - 软件：操作系统软件（系统级别软件）、应用软件（放在系统级别软件上的软件，具有特定功能的软件）
  - 硬件：主板、CPU、声卡、显卡、网卡、内存、硬盘
    - 硬盘：矩形，容量、扇区，永久性保存；硬盘上的文件，用后缀名区分不同的格式；
    - 内存：程序执行时开辟内存，关闭后释放内存
  - 外部设备：耳机、鼠标、键盘（不是计算机必须的组成）

##### 4、JVM和JRE原理

+ 硬盘上存储的不同格式的文件，需要不同的运行环境来支持（比如txt用文本编辑器打开，.doc用word打开，word和文本编辑器就是一个执行该文件格式的环境）

+ Java源文件格式.java（用文本编辑器可以打开），通过虚拟机编译后为.class的字节码文件
+ JRE（Java Runtime Environment，Java运行环境）包含JVM，JVM将.java文件编译成.class文件，JRE提供可以打开.class格式文件的环境
+ JDK：Java Development Kit Java开发工具包，JDK包含JRE，JDK（JRE（JVM））

##### 5、搭建环境

+ JDK：JDK安装程序，官网https://www.oracle.com，下载稳定版本Java SE 8u201/202

+ 查看电脑位数：我的电脑/属性/系统类型

+ 申请Oracle账号，下载后搭建环境

+ 卸载不要直接删除文件夹，因为电脑还有注册表，最好使用设置里的卸载程序

+ javac.exe：bin（binary二进制）文件夹下，编译工具（将Java代码编译成字节码.class文件）

+ java.exe：bin（binary二进制）文件夹下，执行工具（解释器，启动JVM，对.class文件内容进行处理，将机器码编译为机器指令），底层DOS命令窗口看效果，编辑器就是一个带颜色和提示功能的记事本
##### 6、  跨平台机制详解

+ JVM：Java虚拟机，将源文件.java翻译为字节码文件.class文件

+ JRE： Java Runtime Environment运行环境，运行别人写好的程序

+ JDK： 开发工具 Java Development Kit

  - bin文件夹： 全部是工具
  - include文件夹： 包含其他语言写的程序（native修饰符）
  - JRE文件夹：包含运行环境
  - lib文件夹：包含了写好的Java类
  - src.zip：源代码

##### 7、如何编写一段Java源代码（Java文件就是.java）

+ 利用JDK包中提供的工具，进行代码的编译及执行

+ doc命令窗口

+ 用记事本尝试写Java代码

 ```java
class Demo {
    
}
 //class是关键字Java类
 //命名规则：字母、数字（不能为类的开头）、下划线、符号（_ $）
 //不使用中文：字符集不一样反而容易出现乱码，且占用内存较多
 //字母（大小写，敏感）；不会以符号开头，内部类以$开头
 //规约：类名首字母大写，两个以上单词，每个单词首字母大写；起名要语义化较好

 ```

+ 代码的编译执行
  - 编译工具在doc命令窗口：win + R输入cmd打开dos窗口
  - 切换盘符：`d:`盘符名不区分大小写，`cd`切换盘符，切换文件夹`cd ..`退出一层；路径c://Program Files/Java/JDK1.8.0_211/bin/javac
  - 文件和编译工具不在一起：将工具箱放在一个公共位置共同使用，先在当前环境寻找编译工具，然后去共有位置查找工具
  - 配置环境变量：让所有专门后缀的文件都可以使用
    - 最好设置为用户环境变量，自己使用
    - 将Path设置为c://Program Files/Java/JDK1.8.0_211/bin
    - 设置环境变量以后，在什么环境下都可以使用JDK提供的exe执行程序
    - 注意将环境变量中java的环境变量放到最前面，否则容易报错


+ 代码的编译

  - cmd窗口切换到java文件夹下，运行`javac test.java`，会在当前文件夹下生成一个.class文件

```java
    class Demo {
        //主方法，固定写法
        public static void main (String[] args) {
            //public访问权限修饰符，修饰元素是公有的
            //static有且只有一个
            //void表示当前主方法执行完没有返回值
            //main方法名，虚拟机会自己找main
            //String[] args：arguments参数列表
            
            //输出不换行
            System.out.print("I am handsome");
            //输出后换行
            System.out.println("I am handsome 2");
            System.out.println("I am handsome 3");
            //输出结果：I am hansomeI am hansome 2 /n
			//I am hansome 3 /n
        }
    }
```

  - 直接执行`java Demo`即可输出

##### 8、  Java的基本数据类型

1）配置环境变量：Path，让工具可以在任何位置都可以使用

classPath：生成的Demo.class存储在，配置的目的是不管源文件在哪，生成的class文件都统一的存储在配置的目录下（百度学习配置）

JAVA_HOME：目的是为了让路径的写法变得简单（统一的把相同的路径用一个变量保存，相对路径的写法）

```
1.JAVA_HOME : C://program files/java/jdk（公共路径）
path: %JAVA%/bin （子路径）
%JAVA_HOME%就是变量 + /b 拼接路径
```

2）源文件与生成的字节码文件名字不一致：它是以类名进行生成的.class文件，两个名字不同会很难看出来联系，尽量将.java的文件名与里面的类名字相同

```java
//加上public后要求类名与文件名一致,demo.java,demo.class
public class Demo {
    public static void main (String[] args) {
        System.out.println("我真是太帅了！！！");
    }
}
```

3）基本数据类型

8种基本数据类型：

+ 4个整型：byte（字节型），short，int，long

  - byte：字节型，1byte，8bit（敏感的单元位），1byte=8bit，1（符号位）0000000，256种组合，表示数值的范围是-128~127
  - short：2byte，16bit，-32768~32767
  - int：4byte，32bit
  - long：8byte，64bit

+ 2个浮点型：

  - float：4byte，32bit，0（符号位）000000000（9整数部分）000...(小数部分)
  - double：8byte，64bit，第1个表示符号位，后面19位为整数位，其余为小数部分

+ 1个字符型：char 2byte，16位，用单引号区分字符中数字和整数的数字，解决冲突

  - 英文，符号，数字是一个字节

    00000000八位  a--------00000000--------97

    ASCII 美国信息交换标准代码，每一个数字对应一个字母 数字 符号，八位有256种组合（大小写字母，数字，符号的和为26*2 + 10 + 100 = 162，256完全够用，但是中文不够用）

  - 中文是两个字节：

    中文是两个字节，16位，使用Unicode编码

+ 1布尔型：boolean，1bit ，1/8byte，true false，布尔类型与数字类型不能转换

引用数据类型：

+ 数组：[ ]；

+ 类class（抽象类）；

+ 接口interface；

+ 枚举enum;

+ 注解@interface；

```java
public class Demo {
    //源文件是存储在电脑硬盘中的文件，后缀名为.java
    public static void main (String[] args) {
    	    
    }
}
```

4）常量与变量

​	常量：程序运行过程中，不能再次改变的值，作用是：1.固定的值，代表计算过程中经常用到的值，便于程序计算 2.用来代表一个含义，如1，2，3，4代表四个运动方向。所有基本类型的值都是常量3.14、5、'a'、true，特殊常量是字符串，"abc"，String是一个引用数据类型，值很特殊，可以简单视为常量。自己创建的一个空间，存储一个值，让他固定起来，不能改变；

​	变量：变量指的是程序执行过程中可以被改变，变量是内存空间（小容器），变量空间在创建或声明的时候，必须指定数据类型，变量空间的名字，里面只能存储一个内容（值或引用），遵循小驼峰式命名法。见名知义，增强程序的可读性。

​	变量是一个空间，可以只创建空间，不存放内容；空的变量空间不能拿来使用，会产生编译错误。

​	注释的写法：1、单行注释// 	2.多行注释 /* */ 	3.文档注释/**   */（不会参与编译）

​	[^byte x = 1]这个指令，计算机底层做了什么事情：

​	1、硬盘上创建了一个test.java的文件

​	2、文件中的内容是我们编写的源代码（向计算机发送指令）

​	3、将Test.java源文件---->编译----->Test.class

​	4、执行：在内存中执行，，将硬盘上的Test.class内容加载到内存中

​	5、执行内存空间的赋值，存储，变化等

​	6、javac,java的执行程序工作原理图：

![](C:\Users\86180\Desktop\testGit\typoraImg\java文件编译执行原理图.png)


```java
public class Demo {
    public static void main (String[] args) {
        int a = 1;
        byte c = 2;
        //常量缓冲区中会给c分配32bit的内存空间，但是=会进行自动转化，去掉无用的24个0
        
        String b = "abc";
        //字符串用双引号
        
        char f = 'a';
        //字符用单引号，只能写一个字符，不能多写字符
        //注意""与null是不同的
        
        //final定义的常量值不能被更改
        final int UP = 1;
        
        float d = 3.4;
        //执行会报错double转化到float会有损失
        //常量的存储形式是二进制形式存储的，系统为了保持精确程度，常量池会默认给小数分配一个64bit的空间，这时在栈内存（开辟的是32bit的空间），所以存不下就会报错，解决float d = 3.4F；告诉计算机降低精度
        long e = 2147483648;//2的32次方，报错：过大的整数，计算机会认为是你写错了，其实他内存有64bit，所以要告诉计算机我确实需要这么大的整数，long e = 2147483648L;告诉计算机我需要这么大的整数    
    }
}
```

注意：常量缓冲区中整型默认为int(32bit)，小数默认为double(64bit)

5）数据类型之间的转化问题

```java
byte a = 1;//-128~127 8bit
int b = a;//-2147483648~2147483647 32bit 
```

+ 同种数据类型之间是可以直接进行赋值操作的[^int a = 1;int b = a;]
+ 数据类型不同的空间，之间的赋值 ---> 转换问题

> 同种大数据类型之间才能发生转化
>
> 1.基本类型与基本类型之间：可以直接转换（自动、强制）
>
> 2.引用类型与引用类型之间：可以直接转换（自动 强制--上转型 下转型）
>
> 3.基本类型与引用类型之间： 不可以直接转换（间接--包装类/封装类）

```java
int a = 1;//32bit
byte b = a;//8bit
//大空间放小空间是放不进去的

int a = 1;
byte b = (byte)a;//强制类型转换,前提要求int的值不溢出

float x = 3.4F;
double y = x;//会自动补0

double x = 3.4;
float y = (float)x;//会自动压缩空间

int a = 333;//00000000 00000000 00000001 01001101
byte b = (byte)a;//只保留8bit，01001101，十进制77

int a = 1000;//... 00000011强制砍断 11101000
byte b = (byte)a;
//-24,11101000-->取反-->00010111-->加1-->00011000,-24

int a = 1;
float b = a;//1.0，转换规则

float a = 1.9F;
int b = (int)a;//1，直接砍掉小数部分
//整型与浮点型，比较精确程度 浮点型精确程度高 可以直接存放整数 反之需要强制类型转换

char x = 'a';
int y = x;//97

char x = '我';
int y = x;//y是25105

//布尔类型很特殊，不能与其他基本类型进行转化

byte x = 1;
x = x + 2;//报错 
//运行时以整型32bit进行计算，放到8bit的x中报错
//解决：x = (byte)(x + 2)

```

​	总结：

​	1）大数据类型空间可以直接接受小数据类型的值（自动转换）

​	2）小数据类型不可以直接接受大数据类型的值（强制类型转化）

##### 9、Java运算符

运算符：用来指明对于操作数的运算方式

运算符分类：

+ 按照操作数的数目进行分类：

  - 单目++、--，双目+，-，三目？：；

+ 按照运算符功能：

  - 算数运算：+，-，*，/，%，++，--  

    - ++x与x++的区别：

      ```java
      int x = 1;
      int y = x++;//++优先级比=高
      //值传递会产生备份空间
      //x++：做值交换时，先备份，后自增
      //++x：先自增，后备份
      
      int a = 1;
      a = a++;//1
      
      //面试题
      int m = 1;// 2 1 0
      int n = 2;// 3 2 1
      int sum = m++ + ++n - n-- - --m + n-- - --m;
      //sum = 2,m = 0,n = 1;
      ```

  - 赋值运算：= 、+=、 -=、/=、%=（会自动类型提升）

  - 关系运算：==、>=、<=、!=、>、<、instanceof

  - 逻辑运算：&逻辑与、|逻辑或、^逻辑异或、!逻辑非、&&短路与、||短路或

    - &：逻辑与，前后连接的应该是两个boolean的结果
    - |：逻辑或
    - ^：异或，前后结果不一致为true，[^(3>1)^(3>5)  //true]
    - !：将结果取反
    - &&：短路与，当前面结果为false时，后面不再比较，性能比一般逻辑&好
    - ||：短路或，当前面结果为true时，后面不在计算（底层实现是短路），性能比逻辑或|好

  - 位运算（bit）

    - &：按位与

    - |：按位或

    - ^：按位异或

    - ~：按位取反

    - <<：按位左位移

    - ">>"：按位右位移

    - ">>>"：无符号按位右位移

      进制转化问题：

      ![](C:\Users\86180\Desktop\testGit\typoraImg\10进制转2进制.png)

      2进制转化为10进制：

      > 2^5 + 2^4 + 2^3 + 2^2 = 60

      我们为了便于记忆，将二进制分成小单元，进行记忆：

      3个bit记录为一个单元：8进制 [^000 111 100] ,074

      4个bit记录为一个单元：16进制 [^0011 1100],0x3c
    ```java
      3 & 5;
      //..00000011 & ..00000101 --> 00000001 --> 1
      3 | 5;
      // 7
    
    原码：我们计算的码
    反码：正数不变，负数符号不动，其余取反
    补码：负数为反码+1
    
    计算机中不管整数还是负数，存储的形式都是以补码形式进行存储的
    
    6 << 2;//左位移，*2的位移次幂
    //00000110 --> 00011000 --> 24
    
    6 >> 1;//右位移，/2位移次幂
    
    -6 >> 1;//保留符号位置，填1
    //10000110 -- 11111001 -- 11111010 -- 11111101
    //...111 11111010-->...111 11111101
    -6 >>> 1;//不保留符号位置，都填0
//10... 0000110 --11.. 11111001 --11... 11111010 -- 01..1 11111101 
    ```
    
      

##### 10、Java语法结构

```java
//笔试题
1.&与&&的区别：
&前后条件都为true，最终结果就是true，可以视为逻辑运算和位运算
&&当前面条件为false时，发生短路，最终结果为false，只能作为逻辑运算

2.最有效率的方式计算2*8
    计算机2*8过程：
    00000010
   ×00001000
   ----------
    00000000
   00000000
  00000000
 00000010
  -----------
  0000010000(16)
使用乘法，浪费效率
最有效率：2 << 3
5*2//5<<2

3.int a = 1;int b = 2;如何将两个变量的值进行互换
//方式1：采用一个中间变量空间，浪费一个空间
int a = 1;
int b = 2;
int c = b;
b = a;
a = c;

//方式2：不浪费空间，容易产生越界问题
int a = 1;
int b = 2;
a = a + b;
b = a - b;
a = a - b;

//方式3：不浪费空间，也不会产生越界问题
//1^2^2 == 1;
//原理：一个数字异或同一个数字两次，值不会改变
int a = 1;//0000 0001
int b = 2;//0000 0010
a = a^b;//0000 0011
b = a^b;//0000 0001
a = a^b;//0000 0010
```

+ 语法结构：顺序结构、分支结构、循环结构
  - 顺序结构

  - 分支结构：
    - 单分支结构：if...else..

      ```java
      //设计一个小程序 
      //lib提供好的类库 Scanner引用
      Scanner y = new Scanner();
      switch (x) {
          case 1:
              System.out.println("monday");
              break;
          case 2:
              System.out.println("tuesday");
              break;
          ......
      }
      ```

      ```java
      //导包
      import java.util.Scanner;
      //public 要求类名与文件名一致
      public class Test
      	public static void main (String[] args){
      		Scanner input = new Scanner(System.in);
      		System.out.println("请您输入一个数字判断：");
      		int x = input.nextInt();
      		if(x > 100 && x < 150){
      			System.out.println("middle");
      		}else if (x <= 100 && x >= 0) {
      			System.out.println("small");
      		}else if (x >= 150) {
      			System.out.println("large");
      		}
      		else {
      			System.out.println("type not available.");
      		}
      	}
      }
      ```

      ```java
      //猜骰子点数
      import java.util.Scanner;
      public class RandomDice {
      	public static void main (String[] args){
      		//引入库
      		Scanner input  = new Scanner(System.in);
      		//提示玩家输入数字
      		System.out.println("请输入您要猜的点数：");
      		//玩家的输入的数字
      		int assumeNum = input.nextInt();
      		//生成随机点数
      		int randomPoint = (int)(Math.random()*6 + 1);
      		//超出范围的判断（Java类型还不会判断）
      		if (assumeNum > 6 || assumeNum <= 0){
      			System.out.println("请按规定输入1-6之间的数字，谢谢配合！");
      		}
      		else if (assumeNum == randomPoint){
      			System.out.println("666,您猜对了！奖励10分~~~");
      		}else {
      			System.out.print("点数为:" + randomPoint + (char)44);
      			System.out.println("抱歉，您猜错了！积分-10！-_-");
      		}	
      		}
      	}
      ```

      ```java
      import java.util.Scanner;
      public class Season {
          public static void main (String[] args) {
              //345春天，678夏天，9 10 11秋天，12 1 2冬天
              Scanner input  = new Scanner(System.in);
              System.out.println("请输入月份:");
              //nextInt读取整型数字，nextLine()读取字符串
              int month = input.nextInt();
              if (month >= 3 && month <=5){
                  System.out.println("Spring");
              }else if (month >= 6 && month <= 8) {
                  System.out.println("Summer");
              }else if (month >=9 &&  month <= 11 ) {
                  System.out.println("Autumn");
              }else if (month == 12 || month == 1 || month == 2) {
                  System.out.println("Winter");
              }else {
                  System.out.println("Month Error.");
              }
          }
      }
      //最优化的判断，代码量更少
      if(month < 1 || month > 12){
      	  System.out.println("Month Error.");
      }else if (month >= 3 || month <=5){
             System.out.println("Spring");
      }else if (month >= 6 || month <= 8) {
             System.out.println("Summer");
      }else if (month >=9 ||  month <= 11 ) {
             System.out.println("Autumn");
      }else {
            System.out.println("Winter");
                    }
      ```

      写程序应注意的问题：

      1）增强可读性（起名，缩进，注释）

      2）健壮性（严谨，判断时逻辑要严谨）

      3）实现功能的基础上，能不能还优化（空间）

      c语言编程思想：面向过程（不能复用）；Java：面向对象。

    - 多分支结构：switch...case..

      switch(值)，值可以为byte short int char jdk1.5可以判断enum jdk1.7可以判断String。要注意jdk版本

      ```java
      switch (1) {
          case 1:
              System.out.println("monday");
              break;
          case :
              ...;
              break;
          default:
              ...;
      }
      ```

      不写break会将满足的以后的代码都会执行，因为程序必须找到"}"才认为执行结束，根据需要是否使用break。

      if的好处：可以写复杂的逻辑，缺点是每一个else if都会判断，执行较慢

      switch的好处：判断过程效率更高，缺点是只能做固定值的相等判断

      ```java
      //判断学生成绩所在区间
      import java.util.Scanner;
      public class Score {
          public static void main (String[] args) {
              Scanner input = new Scanner(System.in);
              System.out.println("请输入成绩：");
              int score = input.nextInt();
              //101-109判断
              switch (score/10) {
                  case 0:
                  case 1:
                  case 2:
                  case 3:
                  case 4:
                  case 5:
                      System.out.println("不及格");
                      break;
                  case 6:
                      System.out.println("及格");
                   	break;
                  case 7:
                      System.out.println("中等");
                   	break;
                  case 8:
                      System.out.println("良好");
                   	break;
                  case 9:
                      System.out.println("优秀");
                   	break;
                  case 10:
                      if(score==100){
                          System.out.println("满分");
                          break;
                      }  	
                	default:
                      System.out.println("请输入0-100之间的数字");
              }
          }
      }
      ```

      

  - 循环结构：for循环，while循环，do...while...（流程控制）

    - for循环：

      - 变量的声明周期问题：从声明开始创建出来，用完即回收

        ```java
        for(int i = 1;i < 6; i++){
            System.out.print(i);
        }
        System.out.print(i);
        //报错，因为循环结束声明的变量的生命周期结束了
        
        int round = 1;
        for(; round < 6; round++){
            System.out.print(round);
        }
        System.out.print(round);//6
        ```

        小任务：

        1.甲乙丙加工零件，加工零件总数为370个，如果甲加工的零件数多10，乙加工的零件数少20，丙加工的零件数乘2，三个人加工的零件数就相等

        ```java
        //丙是最大的，2*i<370,i<185;
        for(int i = 1;i < 185; i++){
            if(i - 10 + i + 20 + i/2 == 370) {
                System.out.print(i);//144
            }
        }
        ```

        

        2.小鸡，小兔子关在笼子里，小鸡和小兔子总共50只，脚的总数160只，求小鸡和小兔的数量

        ```java
        for(int i = 1;i < 40; i++){
            if(i*2 + (50-i)*4 == 160) {
                System.out.print(i);//20
                break;
            }
        }
        ```

+ 扩展："=="比较的是引用地址，引用数据类型比较相等应该用equals方法

  

##### 11、Java数组的使用

​	数组：Java中数组是数据类型相同的数据的组合，引用数据类型（String也是引用数据类型），数组内存储的类型可以是基本数据类型，也可以是引用数据类型。

​	数组定义（声明）：int[] arr（推荐写法，比较规范）; int x[];int []x;

​	数组的赋值（初始化）：

```java
public class Array {
    public static void main (String[] args) {
        //数组的定义
        int[] arr;
        char[] charArr;
        String[] str;
```

​        

```java
    //静态初始化
    int[] arr = new int[]{10, 20, 30};
    int[] arr = {10, 20, 30, 40};
    
    //取值（访问）
    int value = arr[0];
    System.out.println(value);//10
    arr[6];
    //ArrayIndexOutOfBoundsException数组索引越界
    
    //遍历JDK1.5版本之后新特性，增强for循环，forEach
    for(int val : arr){
        //只能取值，不能存值
        System.out.prinln(val);//10,20,30,40
    }
    
    //动态初始化
    int[] arr = new int[5];//定义数组长度为5
    //整数默认值为0，浮点型默认值为0.0，char默认为0，看不到 String默认为null Boolean 默认为false
}
}
```


​	

基本数据类型与引用数据类型的区别：

​	1）数组是一个引用数据类型

​	2）数组是堆内存中的一串连续的地址存在

​	3）堆内存中的空间长度一旦确定，不能在次改变

​	4）数组内部的存储类型可以是基本的，也可以是引用的数据类型

​	5）数组初始化时必须指定长度及内部存储元素类型

![](C:\Users\86180\Desktop\testGit\typoraImg\引用与基本数据类型存值.png)

​	**小任务：**

​	*1.给定两个数组a{1,2,3,4} b{5,6,7,8}将两个数组内的元素进行互换*

```java
//我的写法
public class ChangeElem {
    public static void main (String[] args) {
        int[] a = {1, 2, 3, 4};
        int[] b = {5, 6, 7, 8};
        for(int i = 0; i < a.length; i++){
            //利用异或：a^b^b == a
            a[i] = a[i]^b[i];
            b[i] = a[i]^b[i];
            a[i] = a[i]^b[i];
        }
    }
}
//老师写法
public class Demo {
    public static void main (String[] args) {
        //1.利用中间变量交换
        int a = {1,2,3,4};
        int b = {5,6,7,8};
        for(int i = 0;i < a.length; i++){
            int x = a[i];
            a[i] = b[i];
            b[i] = x;
        }
        System.out.print(a);//[I015db9742 hashCode
        
//```

        //2.交换地址(交换两个数组中存的堆内存首索引)
        int[] temp = a;
        a = b;
        b = temp;  
    }
}
```



<font color="green">2.给定一个数组a{1,2,3,4,5,6}将数组中元素头尾对应位置互换</font>

```java
public class Demo {
    public static void main (String[] args) {
        int[] a = {1,2,3,4,5,6};
        //a.length/2很精妙
    	for (int i = 0; i < a.length/2; i++){
            int x = a[i];
            a[i] = a[a.length - 1 - i];
            a[a.length - 1 - i] = x;
        }
    }
}
```



*3.给定两个数组合并a{1,2,3} b{4,5}*

```java
public class Demo {
    public static void main (String[] args) {
        int[] a = {1,2,3};
        int[] b = {4,5};
        int len = a.length + b.length;
      	int[] c = new int[len];
        for(int i = 0;i < len ; i++) {
            if(i < a.length) {
                c[i] = a[i];
            }else{
                c[i] = b[i - a.length];
            }
        }
    }
}
```



​	*4.给定一个数组a{1,2,3,9,4,5}*按照数组中最大值位置，将数组拆分成两个

```java
public class ArrayDemo {
    public static void main (String[] args){
        int[] arr = {1,2,3,9,4,5};
        int max = arr[0];
        int index = 0;
        //找到数组中最大值和索引
        for(int i = 1; i < arr.length; i++) {
            if(max < arr[i]){
                max = arr[i];
			    index = i;
            }
        }
        int[] arr1 = new int[index + 1];
        int[] arr2 = new int[arr.length - index - 1];
        for(int j = 0; j < arr.length ; j++) {
            if(j <= index) {
                arr1[j] = arr[j];
            }else {
        //用索引减去上一个数组的长度，后面就能创建新数组
                arr2[j - index - 1] = arr[j];
            }
        }
        for(int k : arr1){
			System.out.println(k);
	}
        for(int l : arr2){
			System.out.println("--" + l);
	}
    }
}
```





​	*5.寻找数组中最大值和最小值{1,2,4,9,3,5,8,7}*

```java
public class ArrayDemo {
    public static void main (String[] args){
        int[] arr = {1,2,3,9,11,4,5,7,8};
        int max = arr[0];
        int min = arr[0];
        for(int i = 1; i < arr.length; i++) {
            if(max < arr[i]){
                max = arr[i];
            }
            if(min > arr[i]){
                min = arr[i];
            }
        }
    }
}
```



*6.去掉数组中的0元素：a{1,2,3,0,0,4,5,0,6,0,7}*

```java
public class ArrayDemo {
    public static void main (String[] args) {
        int[] arr = {1,2,3,0,0,4,5,0,6,0,7};
        //注意要去掉0，去掉0后的长度是7
        int count = 0;
        for(int val : arr){
            if(val == 0){
                count++;
            }
        }
        int index = 0;
        int[] newArr = new int[arr.length - count];
        for(int i = 0; i < arr.length ; i++) {
            if(arr[i] != 0){
                newArr[index] = arr[i];
                index++;
            }
        }
        //清除数组arr在栈内存中的堆内存地址，内存会被GC（garbage collection）回收
        arr = null;
        for(int j : newArr) {
            System.out.println(j);
        }
    }
}
```




​	*7、找到2-100之间的素数*

```java
public class Demo {
    public static void main (String[] args) {
        //素数只能被1和自身整除的数
        int[] arr = new int[30];
        int count = 0;
        for(int i = 2; i <= 100; i++){
            boolean b = false;
            for(int j = 2; j <= Math.sqrt(i); j++){
                if(i%j == 0){
                    b = true;
                    break;
                }
            }
            if(!b){
                arr[count] = i;
                count++;
            }
        }
        int[] newArr = new int[count];
        int index = 0;
        for(int j = 0; j <= count; j++){
           newArr[index] = arr[j];
        }
        for(int k : arr){
            System.out.println(k);
        }
    }
}
```



```

​	*8.数组元素的排序（冒泡、快速、选择、希尔...）*

​```java
public class Demo {
    public static void main (String[] args) {
        //冒泡排序1
        int[] arr = [1,2,4,3,5,6,1];
        //控制比较轮数
        for(int i = 0; i < arr.length - 1; i++){
            //控制每次比较的次数,每次确定一个最大的数
            for(int j = 0; j < arr.length - i - 1; j++){
                if(arr[j] > arr[j+1]){
                    arr[j] = arr[j]^arr[j+1];
                    arr[j+1] = arr[j]^arr[j+1];
                    arr[j] = arr[j]^arr[j+1];
                }
            }
        }
    }
}

public class Demo {
    public static void main (String[] args) {
        int[] arr = [1,2,4,5,3,2];
        for(int i = 0; i < arr.length - 1; i++){
            for(int j = arr.length - 1; j >= i + 1 ; j--){
                if(arr[j] < arr[j-1]) {
                    int temp = arr[j];
                    arr[j] = arr[j-1];
                    arr[j-1] = temp;
                }
            }
        }
    }
}
```



​	*9.用户的登录认证* （用数组当做数据库）

```java
import java.util.Scanner;
public class Demo {
    public static void main (String[] args) {
        //1.注册时将用户名和密码保存到一个数组中
        //2.登录时将用户输入与数组中的数据进行比对
        //先输入账号，因为账号时唯一存在的（主键约束primary key）
        String[] userName = {"陈祥","朱敏","夹克"};
        int[] password = {666,555,888};
        System.out.println("请输入账号:");
        Scanner input  = new Scanner(System.in);
        String user = input.nextLine();
        System.out.println("请输入密码:");
        int pw = input.nextInt();
        boolean key = true;
        for(int i = 0; i < userName.length; i++){
            if(userName[i].equals(user)){
                if(password[i] == pw){
                   key = false;
                   System.out.println("登录成功！~~~"); 
                }
                //提升性能，终止循环
                break;
            }
        }
        if(key){
            //防止提示信息太全，对方知道用户名后破解密码
            System.out.println("用户名或密码错误，请重新核对.");
        }
    }
}
```



​	*10、多维数组*

​	数组：用来存储一组相同类型数据的容器（引用数据类型，存储元素可以是借基本数据类型和引用数据类型）

​	二维数组：一个存储多个小数组的数组

```java
public class Demo {
    public static void main (String[] args) {
        //1.多维数组的定义/声明
        //2.数组初始化（静态/动态）
        int[][] arr = {{1,2},{3,4,5},{6,7}};
        //3.数组元素的访问
        int[] oArr = arr[0];//oArr是hashCode的值
        oArr[0];//1，arr[0][0]
        //4.数组元素的遍历/轮询
        for(int i = 0; i < arr.length; i++){
            for(int j = 0; j < arr[i].length; j++){
                System.out.println(arr[i][j]);
            }
        }
        //增强for循环遍历多维数组
        for(int[] son : arr){
            for(int val : son){
                System.out.println(val);
            }
        }
        
        int[][] array = new int[3][];
        //报错，空指针异常
        
        //三维数组：三维数组实际中少见，因为东西主要存在对象里
        int[][][] array = {{1,2},{3,4},{2,6}},{{5,6},{7,8}},{{9,10}}};
    }
}
```

​	引用类型在内存中的存储结构：

![](C:\Users\86180\Desktop\testGit\typoraImg\二维数组.png)

```java
public class Demo {
    public static void main (String[] args) {
        //面试题
        int[][] array = new int[3][2];
        array[0][0] = 10;
        array[0][1] = 20;
        array[1] = array[0];
        array[0] = new int[4];
        array[1][0] = 100;
        System.out.println(array[0][0]);
        //输出：0
    }
}
```

​	常见的运行时异常：

​		1）InputMisMatchException：出入类型不匹配

​		2）ArrayIndexOutOfBoundsException：数组索引越界

​		3）NegativeArraySizeException：数组长度不合法（长度出现负数）

​		4）NullPointerException：空指针异常（拿来使用会出错，最容易找到，也是最难找的）

​	练习：模拟每个星期教室每一列的同学换位置

```java
import java.util.Scanner;
public class ArrayDemo {
    public static void main (String[] args) {
        int[][] array = {{1,2,3,4},{5,6,7,8},{9,10,11,12},{13,14,15,16}};
        //每周最后一列到第一，其他三列依次换位置
        Scanner input = new Scanner(System.in);
        System.out.println("请输入周数：");
        int week  = input.nextInt();
        //每四周一个循环
        //交换位置 
        for(int i = 0; i < week%4 ; i++){
             //后面的元素前移
             int[] x = array[0];
             for(int j = 0; j < array.length - 1; j++){
				array[j] = array[j+1];
			}
             array[array.length - 1] = x;
        }
        /* //前面的元素后移
        for(int i = 0; i < week%4; i++){
        	int[] x = array[array.length - 1];
        	for(int j = array.length - 1; j > 0; j--){
        		array[j] = array[j-1];
        		}
        	array[0] = x;
        }
        */
        for(int[] arr : array){
            for(int val : arr) {
                System.out.println(val);
            }
            System.out.println("~~~~~~~");
        }
        }
}
```

​	main方法：

​	1）public：访问权限修饰符，共有的，任何地方可以访问到

​	2）static：特征修饰符，静态的，有且只有一份

​	3）void：方法执行完没有返回值，是一个关键字

​	4）main：方法名字，主要的，主方法不是我们调用的，是JVM虚拟机启动的时候，虚拟机调用的

​	5）args：主要是命令行调用Java的时候，可以传参

举例：`java Test chenxiang zhumin`这时args就是一个数组`{"chenxiang","zhumin"}`

```java
public class Demo {
    public static void main (String[] args) {
        System.out.println(args.length);
        for(String val : args){
            System.out.println(val);
            //输出：3，hello，world，myJava
        }
    }
}
//cmd传参： java Demo "hello" "world" "myJava"
```



##### 12、Java编辑器的安装	

> 使用编辑器：提高编码效率
>
> **1、**Eclipse（免费）、MyEclipse（付费编辑器）
>
> 电脑上搭建环境JDK--->配置环境变量--->下载应用程序(www.eclipse.org) --->压缩包，解压，运行eclipse.exe
>
> **2、**破解inteliJ IDEA（功能强大的付费编辑器www.jetbrains.com）
>
> *1）*Dowload下载Java
>
> *2）*根据系统选择系统版本：Windows
>
> *3）*ultimate旗舰版 community社区版
>
> *4）*安装（注意选择64bit）
>
> *5）*勾选Run InteliJ IDEA
>
> *6）*需要注册信息（idea.lanyus.com）
>
> *7）*将[^0.0.0.0 account.jetbrains.com]和[^0.0.0.0 www.jetbrains.com]添加到hosts中
>
> ​	此电脑/windows/System32/drivers/etc/hosts
>
> ​	 将网站中的注册码粘贴到我们勾选的第二种方式下，字体为绿色，就能正常使用了
>
> 8）如果此方法还是不行，下载网站提供的安装包下载地址（可能存在风险）https://idea.lanyus.com/jar/JetbrainsIdlesCrack-3.4-release-enc.jar
>
> ​	将这个安装包放在D:\IntelliJ IDEA 2019.1.2\bin(启动程序的文件夹)文件夹下
>
> ​	修改两个文件：idea.exe.vmoptions ，idea64.exe.vmoptions（使用记事本打开），最后一行添加[^-javaagent:JetbrainsIdlesCrack-3.4-release-enc.jar]
>
> *9）*利用编辑器打开，直接next啥都不勾选（没有过JDK下载JDK，然后new找到所在的文件夹）
>
> *10）*在src文件夹右键new中选择java class
>
> 卸载：不要自己直接卸载，找D:\IntelliJ IDEA 2019.1.2\bin\Uninstall.exe
>
> win + r 输入regedit打开注册表，寻找idea的残留然后删除

##### 13、Java面向对象的编程思想

​	面向过程：大象装冰箱，只能装大象，代码冗余，复用性差；

​	面向对象：

​		*1）*可以装任何符合要求的动物，复用性强，比如开门，关门操作都是一样的。引入开门、关门的代码，然后我们只需要写装狮子等其他动物的代码。

​		*2）*解决问题的时候按照现实生活中的规律来思考问题，考虑问题的过程中，有几个实体参与进来。

​		*3）*类：用来描述一类具有相同特征（属性）和行为（方法）的事物。

​		*4）*对象：具体的事物

​		*5）*计算机中利用面向对象思想来做事

​			先定义一个类（有属性），在描述的类中创建一个具体的个体出来，个体来做事（方法/属性）。

```java
public class Demo {
    public static void main (String[] args) {
        //修饰符 数据类型 属性名字 值
        Person per = new Person();
        per.name = "zhumin";
        per.gender = "female";
        per.age = 18;
        System.out.println("My name is "+per.name+",I am "+per.age+" years old,I am a "+per.gender);
    }
    	Person pe2 = per;
    	per2.name = "bessi";
    	per2.age = 22;
    	per2.gender = "female or male?";
}

public class Person {
    String name;
    String gender;
    int age;
}
```

​	以上代码的流程图：

​	JVM根据项目中的类在方法区创建一个类模板，JVM会自己将主方法塞进执行栈，new的过程在堆内存中创建对象，对象的属性根据模板来画（刚开始默认值name:null,age:0,gender:null），通过方法完成我们想要的事情。

![](C:\Users\86180\Desktop\testGit\typoraImg\类创建对象原理图.png)

​	**方法介绍**：

```java
public class Person {
    public String name;
    public int age;
    public String gender;
    //无参数无返回值的方法
    public void sleep () {
        System.out.println("睡觉~~~");
    }
    //无参数，有返回值
    public String sayName () {
        return this.name;
    }
    //有参数，无返回值
    public void eat (String food,int count) {
        System.out.println("吃了"+count+"碗"+food);
    }
    //有参数有返回值
    public int buyDrinks (String drinkName,int count) {
        int price = 0;
        if(drinkName.equals("GreanTea")){
            price = 5;
        }else if(drinkName.equals("RedTea")){
            price = 3;
        }else{
            System.out.println("drink type is not exist...");
        }
        return count*price;
    }
}

```

​	设计一个方法：画星星

```java
//画星星方法
public void drawStar (int line) {
    /*输入4，打出以下图形：
       *
      **
     ***
    ****
    */
    for(int i = 0; i < line; i++){
        for(int j = 0; j < line - 1 - i;j++){
            System.out.print(" ");
        }
        for(int k = 0; k <= i; k++){
            System.out.print("*");
        }
        System.out.println();
    }
}

//通用，int line控制行数，boolean dir控制方向
public void drawStar (int line,boolean dir) {
    //dir为true，左边开始画星星
    if(dir){
        //控制行数
        for(int i = 0; i < line; i++){
            //控制星星
            for(int j = 0; j <= i; j++){
                System.out.print("*");
            }
            System.out.println();
        }
    }else{
        for(int k = 0; k < line; k++){
            //控制空格
            for(int l = 0; l < line - 1 - i; l++){
                System.out.print(" ");
            }
            //控制星星
            for(int m = 0; m <= k; m++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}

//优化
public void drawStar (int line,boolean dir) {
    for(int i = 0; i < line; i++){
        if(!dir){
            for(int j = 0; j < line - 1 - i; j++){
                System.out.print(" ");
            }
        }
        for(int j = 0; j <= i; j++){
            System.out.print("*");
        }
        System.out.println();
    }
}
```

​	小任务：

​	*1.反向三角形（既可左，又可以偏右）*

​	*2、用来交换两个数组元素 a{1,2,3,4} b{5,6,7,8}*

```java
	//交换数组元素a{1,2,3,4} b{5,6,7,8}
    public void exchangeElem (int[] arr1, int[] arr2){
        for(int i = 0; i < arr1.length; i++){
            arr1[i] = arr1[i]^arr2[i];
            arr2[i] = arr1[i]^arr2[i];
            arr1[i] = arr1[i]^arr2[i];
        }
        for(int val : arr1){
            System.out.println("arr1:"+val);
        }
        for(int val : arr2){
            System.out.println("arr2:"+val);
        }
    }
//缺点：1.循环方式交换数组元素，性能比较慢
//2.交换的时候要保证两个数组元素长度一致
public void changeElem (int[] arr1,int[] arr2) {
    int[] temp = arr1;
    arr1 = arr2;
    arr2 = temp;
}
```



​	*3、用来交换一个数组（头尾互换）*

​	*4、用来寻找给定元素是否在数组内存在*

​	*5、合并两个数组*

​	*6、用来将一个数组按照最大值位置拆分*

​	*7、用来去掉数组中得0元素*

​	*8、用来存储给定范围内的素数（2-100）*

​	*9、用来给数组元素排序，既能升序，又能降序*

​	*10、实现用户登录认证*

​	**总结：**

> 类：抽象笼统的概念，用来描述一组相同的特征和行为
>
> 属性：静态描述类的特征
>
> 属性的定义：权限修饰符 【特征修饰符】 属性类型 属性名字 【=值】
>
> 方法：动态描述类的行为
>
> 方法的定义：权限修饰符 【特征修饰符】 返回值类型 方法名字  (参数名字) 【抛出异常】【{方法执行体}】
>
> 方法的主要结构：方法的参数列表（行为发生的条件），方法的返回值类型（行为发生后得到的结果）
>
> 类的使用：类描述好后，不能直接用来执行，需要通过new的方式创建一个实例，然后才能调用类的方法（执行一次特定行为）和属性（存值和取值）
>
> **<font color="red">注意：方法设计很重要</font>**

```java
publc class Test {
    public int changeNum (int x) {
        x = 100;
        return x;
    }
    public static void main (String[] args) {
    //隐藏过程：加载类模板（此处为Test模板）的过程
    Test t = new Test();
    int a = 1;
    a = t.changeNum(a); //10  
    //堆内存中开辟空间,方法存在对象的内部空间中
    //方法执行时会压到栈内存中执行，并根据传参和内部定义的变量开辟临时空间
    //方法执行完毕后临时空间销毁
    }
}
```

​	方法执行原理图：

![](C:\Users\86180\Desktop\testGit\typoraImg\方法执行内存原理.jpg)

**形参和实参：**

> ```java
> public class Test {
>     public void changeArray (int[] x) {
>     	x[0] = 10;
> 	}
> 	public static void main (String[] args) {
>         //加载Test的类模板
>     	Test t = new Test();
>         //栈中开辟变量t，保存的是指向对象的地址
>         int[] arr = {1,2,3,4};
>         //方法放到栈中执行时，开辟临时内存空间
>         //将栈中的arr地址复制一份到x，指向同一个数组
>         //更改堆内存中第一个元素的值为10
>         t.changeArray(arr);
>         System.out.println("arr[0]:"+arr[0]);//arr[0]:10
> 	}
> }
> ```
>
> 形参：方法执行时的临时变量空间
>
> 实参：方法调用时会将实参的内容传递给形参（<font color="red">常量传递的是值，引用数据类型传递的是值</font>）

  