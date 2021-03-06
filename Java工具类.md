### Java工具类

<hr>

##### 1、枚举

引用数据类型：数组，类，抽象类`abstract class`，接口`interface`，枚举，注解`@interface`



枚举类：一个类中的对象，认为个数是有限且固定的，可以将一个对象都列举出来

Enum类型：

两个属性，name()获取name的属性，ordinal()获取序号，类似index

常用方法：`valueOf`()获取对应的枚举对象、`values()`获取所有的枚举对象、`compareTo()`、`toString()`

```java
//JDk1.5版本以后增加的枚举类
public class Demo {
    private Demo (){}
    public static final Day monday = new Day();
    ...
    public static final Day sunday = new Day();
}

public class Test {
    public static void main (){
        Day d = Day.monday;
        ...
    }
}

//枚举类使用
//每一个enum类型的类，会默认继承Enum,枚举类型不能继承其他类
public enum Demo {
    //系统内部做了private staic final
    monday,tuesday,wendesday,thursday,friday,saturday,sunday
}

public class Test {
    public static void main (String[] args){
        Demo d = Demo.monday;
        //下面由很多方法
    }
}
```

输入一个日期的英文单词，输出中文：

```java
import java.util.Scanner;
public enum Day {
    monday("星期一",1),tuesday,wednesday,
    thursday,friday,saturday,sunday
    private Day (String name,int index){
        this.name = name;
        this.index = index;
    }
    public String getName (){
        return this.name;
    }
}
public class Test {
    public static void main (String[] args){
        Scanner input = new Scanner(System.in);
        String key = input.nextLine();
        Day day = Day.valueOf(key);
        switch (day) {
            case monday:
                System.out.println("星期一");
             ...
            default:
                System.out.println("输入单词有误.")
        }
    }
}
```

##### 2、内存机制问题

通过new的指令创建的对象在堆内存中存储，通过Garbage Collection回收

GC是一个线程，用来回收堆内存中的垃圾

```java
public class Person {
    //重写Object的finalize方法，用来回收
    public void finalize () {
        System.out.println("垃圾回收了");
    }
}
public class Test {
    public static void main (String[] args){
        Person p = new Person();
        p = null;
        System.gc();
    }
}
```



Runtime类：

`maxMemory()`堆的总内存

`totalMemory()`堆开辟的可使用的内存

`freeMemory()`堆开辟的内存中空闲的内存

Runtime图解：

![](C:\Users\86180\Desktop\testGit\typoraImg\堆内存的开辟.png)

```java
Runtime r = Runtime.getRunTime();
//返回值为long类型
long max = r.maxMemory();
long total = r.totalMemory();
long free = r.freeMemory();
```

堆内存溢出：`OutOfMemoryError`堆内存溢出错误



##### 3、包装类

​	包装类也可以称为封装类，Java开发者写好的类

​	八个包装类都在`java.lang`包下，不需要import导包

​	文档下载：

​	https://docs.oracle.com/javase/8/docs/api下载`javaAPIs`

​	包装类：`byte--Byte`,`char--Character`,`short--Short`,`int--Integer`,`long--Long`,`boolean--Boolean`,`float--Float`,`double--Double`

​	拆包：`intValue()`,`floatValue()`等等

```java
public class Test {
    public static void main (String[] args){
        //1.Integer.parseInt()
        int a = Integer.parseInt("123");
        int i = new Integer("abc");
        //NumberFormatException数字格式化异常
        //JDK1.5以前需要拆装
        Integer i1 = new Integer(10);
        int value = i1.intValue();
        //常见面试题
        Integer i1 = 10;
        Integer i2 = 10;
        Integer i3 = new Integer(10);
        Integer i4 = new Integer(10);
        System.out.println(i1 == i2);//true
        System.out.println(i1 == i3);//false
        System.out.println(i3 == i4);//false
        System.out.println(i1.equals(i2));//true
        System.out.println(i1.equals(i3));//true
        System.out.println(i3.equals(i4));//true
        //==比较地址，equals比较值的大小
        //这个equals是Integer重写的方法，不是Object的方法
        //如果i1改为1000，发现i1==i2为false
        //-128~127比较的是默认初始化到缓存中的地址，超过这个值的声明会重新创建一个新对象
    }
}
```



###### （1）数学相关

​	在java.lang包下，Math构造方法是私有的，不能直接调用创建对象

​	常用Math的方法：

> 1.`Math.abs()`返回值为`double`类型
>
> 2.`Math.floor()`返回值为`double`类型
>
> 3.`Math.ceil()`返回值为`double`类型
>
> 4.`Math.rint()`返回值为`double`类型，如果两边距离一样则返回偶数
>
> 5.`Math.round()`返回值是`int`或者`long`类型，`float`就是`int`类型，`double`就是`long`类型
>
> 6.`Math.pow(a,b)`参数是double类型，返回值也是double类型
>
> 7.`Math.max()`,Math.min()找两个值中小的一个
>
> 8.`Math.sqrt()`参数是double类型
>
> 9.`Math.random()`返回值是double类型

```java
0-9的随机整数
(int)(Math.random()*10);

5.0-10.9的随机数
Math.random()*6+5;
//Math.random()在小数上可能存在一些问题比如0.0~5.4999

使用Random()包，使用如下：
1.位置java.util.Random;
2.没有任何继承关系，默认继承Object类
3.查找构造方法-->如何创建对象
import java.util.Random;
Random r = new Random();
int val = r.nextInt();//范围是整型数据的范围-2147483648-2147483647
int val2 = r.nextInt(10);//[0-10),[0,bound)bound必须是正数
//bound为负数：IllegalArgumentException
float f = r.nextFloat();//[0.0,1.0)

UUID类：没有任何继承关系
import java.util.UUID;
UUID uuid = UUID.randomUUID();
uuid.toString();
//随机产生一个32位的16进制数,用来做数据库表格主键

BigInteger类
//大整数 java.math包 需要Import导入 都是数组实现的 继承自Number
BigDecimal
BigInteger bi1 = new BigInteger("13412");
BigInteger bi2 = new BigInteger("13412342");
//类中常用的方法，做四则运算
bi1.add(bi2);
bi1.subtract(bi2);
bi1.multiply(bi2);
bi1.divide(bi2);

//保留两位小数，向下取
BigDecimal bd = new BigDecimal("3.4562");
bd.setScale(2,BigDecimal.ROUND_DOWN);

//java.text包
DecimalFormat df = new DecimalFormat("000.###");//数字表示不够位数补数字，#表示不够不补，多了只保留三位
String value = df.format(123.456789);//123.457四舍五入

```

System类在`java.lang`包下，`out`输出、`in`输入、`err`、`currentTimeMillis`获取当前毫秒数，`gc()`通知垃圾回收

> ```java
> long time = System.currentTimeMillis();
> ```



###### （2）日期相关

Date()被废弃了，没有考虑时区，被calender类取代

```java
Date d = new Date(1558860322483L);
Date d2 = new Date();//废弃的意思，不推荐使用
System.out.println(d);
System.out.println(d.before(d2));//d是否在d2前，返回一个布尔值
d.setTime(1558860323000L);//设置时间
d.getTime();//获取时间（毫秒）
d.compareTo(d2);//按照创建的顺序比较，1后创建，-1之前创建
//DateFormat是一个抽象类，在java.text包下，SimpleDateFomat是重写了的具体类
DateFormat sdf = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");//多态
System.out.println(sdf.format(new Date()));//2019-05-26 04:59:25
//Calender类，在java.util包下
Calendar c = Calendar.getInstance();
//常用方法：
//1.after()
//2.before()
//3.getTimeZone()时区相关信息
//4.set()设置某一个
//5.get()获取某一个
Calendar c = Calendar.getInstance();
System.out.println(c);//c是JSON格式
int year = c.get(Calendar.YEAR);
int month = c.get(Calendar.MONTH);//月份从0开始计算的
int day = c.get(Calendar.DAY_OF_MONTH);
c.set(Calendar.YEAR,2015);//将年份设置位2015年
System.out.println(year + ":" + month + ":" + day);//2019:4:26
TimeZone tz = c.getTimeZone();//TimeZone.getDefault()
System.out.println(tz.getID());//Asia/Shanghai
tz.getDisplayName();//中国标准时间
```

**<font color="red" size="4">以下类很重要:</font>**

###### （3）字符串

所属包在`java.lang`包下，不需要引入，和其他语言都是用字符串传递的，所以很重要



String比较的原理图：

![](C:\Users\86180\Desktop\testGit\typoraImg\String的比较.png)

String的特性：

1）常见的String的笔试题：==与equals的区别，String的不可变特性，String与StringBuffer区别，StringBuffer与StringBuilder的区别

2）实现了Serializable，CharSequence，Comparable三个接口

3）如何构建对象：

> 1、创建方法
>
> String str = "abc"; `直接赋值（在字符串常量池）
>
> `String  str = new String("abc");`利用构造方法创建String对象
>
> `String str = new String(byte[] c);`利用byte数组创建字符串，将数组中的每一个数字转化成对应的char，组合成String
>
> `String str = new String(char[] c);`利用char数组创建字符串
>
> 2、常用的方法
>
> （1）`equals()`比较字面值是否相等（重写了Object的equals方法）
>
> （2）`hashCode()`重写了Object的`hashCode`方法（31*h 的和）
>
> 3、String的不可变性
>
> 体现在长度和内容上
>
> ​	长度：final修饰的数组，数组长度本身不变，final修饰数组的地址也不变
>
> ​	内容：private修饰的属性，不能在类的外部访问
>
> ```java
> //String类中的定义
> private final char[] value;
> //但是每一个字符是可以改变的
> ```
> 
> **字符串的内容是存储在方法区的常量池里面的，是为了方便字符串的重复使用**
>
> 4、String类的判断功能
>
> ```java
>equals(Object obj);
> equalsIgnoreCase(String str);//忽略大小写进行判断
> startsWith(String str);//判断字符串对象是否以str开头，用来判断文件开头
> endsWith(String str);//判断字符串对象是否以st结尾，用来判断文件后缀名
> ```
> 
> 5、模拟用户登录
> 
> ```java
>package logindemo;
> import java.util.Scanner;
>public class Login {
> private String[][] arr = {{"zs","111"},{"ls","222"},{"zhuminmin","666"},{"admin","admin123"}};
> private int count = DEFAULT_COUNT;
> private static int DEFAULT_COUNT = 3;
> public Login () {}
> public Login (int inputCount ){
> this.count = inputCount;
> }
> public void start() {
> //控制输入的次数
> boolean a = false;
> for(int i = 0; i < this.count;i++){
> Scanner input = new Scanner(System.in);
> System.out.println("请输入用户名：");
> String userName = input.nextLine();
> System.out.println("请输入密码：");
> String password = input.nextLine();
> for(int j = 0; j < arr.length; j++){
>  if(arr[j][0].equals(userName)&&arr[j][1].equals(password)){
>      System.out.println("登录成功");
>      a = true;
>      break;
>     }
>    }
>    if(a){
>     break;
>    }else{
>  if(this.count - i - 1 == 0){
>      System.out.println("登录失败，请与管理员联系");
>     }else{
>      System.out.println("用户名或密码错误，你还有"+(this.count-i-1)+"次机会");
>     }
>    }
>    }
>    }
>    //主方法
> public static void main (String[] args){
> Login  l = new Login();
> l.start();
> }
> }
> 
> 
> ```
> 
> 6、字符串的获取功能
> 
> ```java
>int length()//获取字符串的长度
> char charAt(int index)//获取指定索引的字符
>int indexOf(String str)//获取str在字符串对象中第一次出现的索引
> String substring(int start)//从start位置截取字符串
> String substring(int start,int end)//从start处截取字符串到end结束，不包含最后一位
> 
> int compareTo(String str);
> //按照两个字符串长度较短的那个作为循环的次数，挨个比较
> //循环内有结果，返回结果，否则比较长度
> //实现自Comparable接口
> 
> String toString();//重写了toString方法
> //public String toString() {return this;}
> 
> String concat();//将给定字符串拼接在当前字符串后面
> //因为原数组地址不能改变，长度固定，多以返回的是一个新的String对象
> //concat方法的性能比拼接的方法性能快很多
> //concat方法：不会在常量池中拼接产生一个新的对象
> //StringBuffer拼接效率非常高，没有用final修饰，可以不断扩容，频繁拼接使用StringBuffer
> 
> boolean contains(CharSequence);//判断是否包含一个字符串，返回一个布尔值
> 
> byte[] getBytes();//将字符串拆成一个byte数组
> 
> char[] toCharArray();//将字符串拆成一个char数组
> 
> int indexOf(str,fromIndex);//找寻字符在字符串中第一次出现的位置索引，第二个参数是从指定索引开始找
> 
> int lastIndexOf();//从数组末尾开始找
> 
> String replace();//所有出现该串的地方全换
> String replaceAll();//全换
> String replaceFirst();//只换第一次出现的字串
> 
> String[] split(String regex,int limit);//拆分字符串
> String toUpperCase();//转换成大写
> String toLowerCase();//全部转成小写
> String trim();//去掉字符串前后多余空格
> 
> String.valueOf(char c);//将字符变字符串
> 
> 
> ```

4）String的作业

> 字符串作业：
>
> 1.设计方法将字符串反转
>
> ```java
> public String reverse (String str){
> char[] charArr = str.toCharArray();
> for(int i = 0; i < charArr.length/2; i++){
>   char temp = charArr[i];
>   charArr[i] = charArr[charArr.length-i-1];
>   charArr[charArr.length-i-1] = temp;
> }
> return new String(charArr);
> }
> 
> ```
> 
>
> 
>2.将指定字符串的正序和反序进行连接 ok->okko
> 
>```java
> public String reverseAndConcat (String str){
> return str.concat(this.reverse(str));
> }
> //return str.concat(this.reverse(str));
> ```
> 
> 
> 
>3.判断给定字符串是否回文 abccba abcba
> 
>```java
> public boolean isPalindrome (String str) {
>if(this.reverse(str).equals(str)){
> return true;
> }
> return false;
>   }
> ```
> 
> 
> 
> 4.将给定字符串右移x位置 helloworld -> ldhellowor
> 
>```java
> public String moveToRight (String str,int count){
>//截取
> if(count > str.length()){count %= str.length();}
>String begin = str.substring(0,str.length()-count);
> String end = str.substring(str.length()-count);
> return end.concat(begin);
> }
> ```
> 
> 
> 
> 5.寻找若干字符串中最长的那个
> 
> ```java
> public String findMax (String...strArr){
>String result = strArr[0];
> int maxLength = strArr[0].length();
>for(int i = 0; i < strArr.length; i++){
> if(strArr[i].length() > maxLength){
>maxLength = strArr[i].length();
> result = strArr[i];
> }
>    }
>    return result;
> }
>   ```
>    
>    
>   
> 6.统计给定字母在字符串中出现的次数
> 
> ```java
> //方法1：
> public int letterExistCount (String str,char c){
> int count = 0;
>for(int i = 0; i < str.length(); i++){
> if(str.charAt(i) == c) count++;
>}
> return count;
>}
> 
> //方法2
> return str.length() - str.replace("c","").length();
> 
> 
>   ```
> 
> 
> 
> 7.将给定的字符串每一个首字母大写
> 
> ```java
> public String letterFirstToUpperCase (String str){
> String[] strArr = str.split(" ");
> String result = "";
>for(int i = 0; i < strArr.length; i++){
> String value = strArr[i];
>result = result.cancat(value.substring(0,1).toUperCase().concat(str.substring(1)));
> }
>return result;
> }
> ```
> 
> 
> 
>   8.获取给定字符串中的全部数字（返回`int`类型）
>   
> ```java
> public int getAllNumerInString (String str){
> String result = "";
> for(int i = 0; i < str.length(); i++){
> int value = str.substring(i,i+1).codePointAt();
> if(value > 47 && value < 58){
>result = result.concat(String.valueOf((char)value));
> }
>}
> return  Integet.parseInt(result);
>   }
> ```

**<font color="pink">5)</font>**	StringBuffer与StringBuilder的区别

> （1）String与StringBuffer与StringBuilder的区别
>
> String：Serializable，CharSequence，Comparable
>
> StringBuilder和StringBuffer：Serializable，CharSequence，Appendable
>
> String是不可变字符串，StringBuilder是可变字符串
>
> String具有不可变性，频繁修改内容时性能不太好
>
> （2）StringBuffer/StringBuilder没有compareTo方法，新增了append方法
>
> （3）StringBuilder/StringBuffer的常用方法：
>
> ```java
> StringBuilder builder = new StringBuilder();
> //最主要的方法，append方法，用来做字符串拼接速度非常快
> int capacity();//返回扩容的后的数组长度
> int length();//返回字符串的长度
> char charAt();//返回指定索引的字符
> StringBuilder setCharAt(int index,char c);//改掉某一索引的字符
> int codePointAt();//返回字符的编码
> //StringBuilder中独有的方法
> StringBuilder delete(int start,int end);//删除元素,不用接收返回值
> StringBuilder deleteCharAt(int index);//删除指定索引位置的字符
> StringBuilder insert(int index,String str);//插入方法
> StringBuilder replace(int start,int end,String str);//替换
> StringBuilder setLength();//手动设置字符串长度，不安全
> String toString();//将StringBuilder对象构建成一个String对象返回
> StringBuilder trimToSize();//将数组中无用的容量清除，去除的时多开辟的内存容量
> ```
> 
> （4）符串频繁拼接的时候，我们使用StringBuilder
>
> （5）StringBuilder与StringBuffer区别：
>
> StringBuilder（JDK1.5）是StringBuffer（JDK1.0）出的更新版本，使用方法几乎一致
>
> 早期版本都是线程安全的，所以StringBuffer是线程安全的，方法都带修饰符synchronized(同步)
>
> StringBuilder效率更高，可以支持异步访问

6）正则表达式

> 1、正则表达式：一个带有一定规律的表达式，匹配字符串格式的
>
> 2、正则的作用
>
> ​	（1）字符串的格式校验	String中方法matches("regexp")
>
> ​	（2）字符串的拆分及替换	String中方法replace和split
>
> ​	（3）字符串的查找	Pattern模式	Matcher适配器
>
> 3、正则的使用
>
> ```java
> 描述字符信息：
> \d:表示0-9的数字，digit
> \s:表示space，留白（空格，回车，换行都是）
> ".":表示任意字符
> \w:表示一个数字或字母[0-9A-z]
> 
> 描述字符出现的次数：
> ？：0-1次
> *：0次以上
> +：1次以上
> {n,m}:出现n-m次
> 
> 查找：
> String str = "432143abcr1rewabcrer858713*420117";
> //创建模式对象
> Pattern pattern = Pattern.compile("\\d{6}");
> //创建一个匹配器
> Matcher matcher = pattern.matcher(str);
> //找寻
> while(matcher.find()){
> System.out.println(matcher.group());
> }
> 
> 
> ```



###### **<font color="red">（4）集合相关</font>**

集合：集合是指具有某种特性的具体或抽象的对象汇总而成的集体。

集合是一个容器，用来存储一组元素，集合的长度存储之后还能改变

集合的两个分支：collection接口（存储的都是value对象），Map接口（存储的是以key-value形式存在）

collection的子分支：List和Set

**1）List**

有序可重复，ArrayList（1.2）、Vector（1.1线程安全）、LinkedList

特点：适合遍历和轮询，不适合插入和删除，底层为数组

> （1）交集：addAll(ArrayList<E> list);
>
> （2）差集：removeAll(ArrayList<E> list);
>
> （3）交集：retainAll(ArrayList<E> list);
>
> （4）截取：List subList()

```java
ArrayList list = new ArrayList(int initialCapacity);
//我们设置初始值性能会更好，不断扩容会消耗性能
//默认长度10个
list.add("a");
list.add("b");
//由于ArrayList底层是一个Object[]，什么类型都可以传，取出来还需要造型，太麻烦
//JDK1.5出了泛型解决问题
ArrayList<String> list = new ArrayList<String>();

1.添加元素add
list.add("a");list.add("b");list.add("c");

2.遍历
for(int i = 0; i < list.size(); i++){
    System.out.println(list.get(i));
}
System.out.println(list);//[a,b,c]

3.删除元素remove
for(int i = 0; i < list.size(); i++){
    list.remove(i);//list.remove(0)都删除不干净
}
解决办法：
int size = list.size();
for(int i = 0; i < size; i++){
    list.remove(0);
}

4.插入
list.add(int index,Collection c);//将一个子类插到指定索引位置去
lsit.addAll(int index,Collection c);

5.清除
list.clear();//清除集合中所有元素
list.remove(int index);
list.remove(Object o);
//传入数字的时候，不会包装，默认删除指定索引元素

lsit.removeAll(Collection c);//差集，删除list中出现在c中的元素
list.retainAll(list2);//交集，共有的元素
list.addAll(list2);//并集

6.查找
list.contains(Object o);
E list.get();

7.迭代器
boolean list.iterator();

8.转化成数组
Integer x = new Integer[list.size()];
<A> list.toArray(x);

9.消除多余空间
list.trimToSize();//消除多余空间

10.截取
List list.subList(int fromIndex,int toIndex);//截取不包含最后一个元素


```



泛型：

1、泛型类：类定义的时候描述某种数据类型，集合的使用就是这样

2、泛型接口：与泛型类使用基本一致，子类实现接口时必须加泛型

```java
public abstract class ArrayList<E> extends AbstractList {}
public class ArrayList<E> extends AbstractList {}
```

3、泛型方法：方法调用时传参数，方法的泛型与类无关，带有泛型的方法可以不放在泛型类里

4、泛型不能使用基本类型，如果想使用基本类型，需要使用其对应的基本类型

```java
ArrayList<Integer> list1 = new ArrayList<Integer>();
ArrayList<Integer> list2 = new ArrayList<Integer>();
list1.addAll(list2);
//源码：list1.addAll(Collection<? extends E> list2)
//同类型，或者是该类型子类，即可添加，否则不能添加
```



Vector：（线程同步，早期的版本）ArrayList（线程不安全，后期版本的Vector）

默认扩容2倍，多了个修饰符`synchronized`



数据结构图：

![](C:\Users\86180\Desktop\testGit\typoraImg\数据结构.png)



Stack类（栈）

- 在java.util包下
- 继承Vector，可以使用Vector的方法
- 构造方法只有一个参数
- Stack的独有方法：
  - `push()`	将某个元素存进栈
  - `pop() `    将某个元素剪切出来
  - `peek() `   查看栈顶的一个元素
  - `search(<E> o) ` 查找给定元素在栈中的位置
- 使用场景：
  - 撤销功能
  - 中国象棋的悔棋功能







Queue类（队列，接口）

- 接口：实现了Collection接口，并且有`LinkedList`子类，`ArrayDeque`
- 通常无参数构造方法创建
- Stack的方法都有，独有方法：
  - `offer()`添加元素，可以返回异常
  - `poll()`删除元素，从最后一个删除
  - `peek()`查看底部的元素
- 使用场景：
  - 火车站排队买票功能



LinkedList类

- 在java.util包下

- 使用双向链表的数据结构形式来存储，不适合遍历和轮询

  ```java
  //ArrayList和LinkedList可以通过构造方法转化，但是参数的类型必须比目标的泛型小
  ArrayList<String> arr = new ArrayList<>();
  arr.add("chen");
  arr.add("xiang");
  arr.add("handsome");
  LinkedList<Object> link = new LinkedList<Object>(arr);
  System.out.println(link);
  ```
  
- 插入删除速度特别快，遍历比较慢，因为地址无序，找地址浪费性能



2）Set

- 无序无重复，具体实现类：
  - hashSet：结构式hashMap（数组加链表，散列表）
    - 在java.util包下，无序
- 基本使用
  - 无序无重复作用的方法：`equals`、`hashCode`

> **<font color="red">无重复原则：先用hashCode进行地址的比较，然后用euqals进行比较，都相同拒绝存入，不是覆盖</font>**
>
> 1.boolean add(value);
> 2.boolean remove(value);
> 3.可以使用增强for循环遍历
> 4.toArray();将集合转化为数组
> 5.iterator();获取一个迭代器对象（增强for就是迭代器实现的）
> 6.size();获取有效元素个数

```java
public class Test {
    public static void main (String[] args){
        HashSet<Person> p_set = new HashSet<Person>();
        p_set.add(new Person("chenxiang"));
        p_set.add(new Person("chenxiang"));
        p_set.add(new Person("chenxiang"));
        //不重写输出3，比较的是变量空间，因为Person中重写了equals方法，hashCode方法
        //System.out.println(p_set.size());3
        //System.out.println(p_set);
        //无重复原则：利用equals方法进行比较
        //让Person对象的name一致，认为是同一个对
        //set集合拒绝重复的元素,所以取出来的就是第一个
        HashSet<String> iset = new HashSet<String>();
        iset.add("a");
        iset.add("a");
        iset.add("a");
        System.out.println(iset.size());//1
    }
}

public class Person {
    private String name;
    public Person (String name,int age){
        this.name = name;
        this.age = age;
    }
    public String getName (){
        return this.name;
    }
    //重写equals方法，但是还是没有改变size，因为还得重写hashCode
    public boolean equals (Object o){
        //如果地址xiang
        if(this==o){
            return true;
        }
        if(o instanceof Person){
            Person p = (Person)o;
            //使用字符串的equals方法
            if(this.name.equals(p.name)&&this.age == o.age){
                return true;
            }
        }
        return false;
    }
    public int hashCode (){
        //两个对象的name一致，需要让hashCode的返回值一致
        //使用字符串重写的hashCode方法，字符*31+h
        return this.name.hashCode();
    }
    //方便我们输出，不适用对象的toString方法，因为看不懂
    public String toString () {
        //使用StringBuilder提高拼接性能
        StringBuilder sb = new StringBuilder();
        sb.append("{");
        sb.append(this.name);
        sb.append("}");
        return sb.toString();
    }
    
    //使用treeSet必须重写compareTo方法,implements Comparable<Person>
    @Override
    public int compareTo (Person o){
        //compareTo比较的是长度和字母，treeSet根据返回值确定顺序
        //我们自定义规则名字相同且
       int value = this.name.compareTo(o.name);
       if(value != 0){
            return value;
        }
        return this.age - o.age;
    }
}


```



- - treeSet
    - 二叉树，利用Node（left，item，right，parent）
    - java.util包
    - treeSet本身有顺序，使用的是compareTo，按照字母的自然顺序排布
    - 不能随意存储，让自己的类实现Comparable接口，根据`compareTo()`的返回值进行排序

- 特点：适合插入和删除，不适合遍历和轮询，底层为链表

- 基本使用：与Set中代码相同，增加了compareTo方法，利用它的返回值确定顺序

  ```java
  TreeMap<Test> map = new TreeMap<Test>();
  
  public class Test {
      public String name;
      public int age;
      public Test (String name,int age){
          this.name = name;
          this.age = age;
      }
  	public compareTo (Test obj) {
          int value = this.name.compareTo(obj.name);
          if(value!=0){
              return value;
          }
          return this.age - obj.age;
      }
  }
  
  ```



**3）Map<K,M>**

key无序无重复，value无序可重复

- 映射：通过某一个key定位到一个value
- Map的基本使用（包名java.util）：
  - hashMap：key的存储顺序与取的顺序不同，不同键名可以存相同的值，key相同值会进行覆盖，而不是像set拒绝存入
  - map集合使用场景：长度不确定，用集合，可以通过键名快速定位元素；Hash性能更高,Tree希望存进去的元素自动排序
  - List：有序，存储有序使用List；ArrayList遍历轮询；linkedList适合插入删除,Stack先进后出，Queue先进先出
  - Set：无序无重复，存储元素希望去掉重复元素；Hash性能更高,Tree希望存进去的元素自动去重复且自动排序
  - <font color="red">HashSet重复元素拒绝存入，HashMap重复元素进行覆盖</font>

```java
value add(key,value);//第二次添加相同键值会覆盖

E remove(key);//删除
boolean remove(key,value);

replace(key,value);//改，和put方法一样
E get(key);//获取元素

int size();//返回存储元素的个数

boolean contains(key);//是否包含键名
boolean contians(value);//是否包含键值

Set keySet();//获取全部的key，entrySet();获取全部的entry(Node)对象

E getOrDefault(key,defaultValue);
putIfAbsent();//key不存在就存入，存在就放弃

遍历：
HashMap<Integer,String> map = new HashMap();map.add(1,"a");
map.add(1,"b");map.add(1,"c");map.add(1,"d");
//将键名转成set
Set<Integer> keys = map.keySet();
//通过迭代器遍历keys
Iterator<Integer> it = keys.iterator();
while(it.hasNext()){
    int key = (Integer)it.next();
    String value = map.get(key);
    System.out.println("key:"+key+";value:"+value);
}

```

- TreeMap：以二叉树形式存储，自然有序，按照unicode编码排序
  - 底层数据结构的存储：JDK1.8版本红黑二叉树（层级多于两层，顶节点会改变，使结构稳定，左旋右旋）
  - 使用与hashMap一致

```java
TreeMap<Integet,String> map = new TreeMap<Integer,String>();

map.put(1,"a");
```

考试系统：

```java
/*
 1.考试的题目如何存储？
 2.类与类之间的关系
 题目：属性title，answer
 考试机：属性题库，存储好多个Question对象
*/
public class Question {
    private String title;
    private String answer;
    public Question (String title,String answer){
        this.title = title;
        this.answer = answer;
    }
    public String getTitle (){
        return this.title;
    }
    //重写比较方法，根据题目开头判断题目的问题是否重复
    public boolean equals (Object obj){
       if(this == obj)return true;
       if(obj instanceof Question){
           Question q = (Question)obj;
           String[] titleArr = this.title.split("?");
           String[] anotherStrArr = q.getTitle().split("?");
           return titleArr[0].equals(anotherStrArr[0]);
       }
       return false;
    }
    //返回题目问题的hashCode
    public int hashCode (){
        String[] titleArr = this.title.split("?");
        return this.titleArr[0].hashCode();
    }
}
//使用Set存储，重写equals和hashCode方法
public class Machine {
    private HashSet<Question> questionSet;
    {
        添加题目
    }
    //深入理解随机出题的精妙
    public ArrayList<Question> getPaper () {
        //存取题目的Set集合
        HashSet<Question> paper = new HashSet<Question>();
        //利用Collection接口要求子类实现的互相转化功能
        ArrayList<Question> questionSet = new ArrayList<Question>(this.questionSet);
		while(paper.size()!=5){
         //假设size是20，返回0-19的整数
   	 	int index = new Random().nextInt(this.questionSet.size());
    	paper.add(questionSet.get(index));
    	}
    	return new ArrayList<Question>(paper);
}

public class Student {
    private String name;
    public student (String name){
        this.name = name;
    }
    public String[] exam (ArrayList<Question> paper){
        String[] answer = new String[paper.size];
        for(int i = 0; i < paper.size(); i++){
            Question question = paper.get(i);
            System.out.println(question);
            System.out.println("请输入你的答案：");
            answer[i]  = input.nextLine();
        }
        return answer;
    }
}
```

***深入理解随机代码：***

```java
public class Machine {
    private HashSet<Question> questionSet;
    {
        添加题目
    }
    //深入理解随机出题的精妙
    public ArrayList<Question> getPaper () {
        //存取题目的Set集合
        HashSet<Question> paper = new HashSet<Question>();
        //利用Collection接口要求子类实现的互相转化功能
        ArrayList<Question> questionSet = new ArrayList<Question>(this.questionSet);
        //当元素存入够5个的时候停止循环
		while(paper.size()!=5){
         //假设size是20，返回0-19的整数
   	 	int index = new Random().nextInt(this.questionSet.size());
         //随机数可能出现相同的数，但是利用HashSet的拒绝重复元素存入特性，所以题目不会重复
    	paper.add(questionSet.get(index));
    	}
    	return new ArrayList<Question>(paper);
}
```



###### （5）异常相关

​	1）错误/异常：程序运行过程中，可能发生一些不被期望的效果，肯定会阻止我们的程序按照指令去执行

​	2）规定的接口：`Throwable`，再java.lang包下

​	3）实现Throwable接口的重要子类

- `Error`：错误，通常是物理性的，JVM虚拟机本身出现问题。程序指令处理不了
- `Exception`：异常，人为规定不正常的现象，通常是给定的程序指令产生不符合规范的事情
- 运行时异常：运行时异常（非检查异常），`RuntimeException`
  - `Error`和`RuntimeException`都算是运行时异常
  - 整数除0产生数学异常，小数除0产生无穷
- 编译时异常（检查异常）
  - `InterruptException`，eg:`Thread.sleep(5000)`
  - 处理异常的手段：解决运行时异常，让后续代码可以继续执行

```java
package bank;

public class Test {
    public static void main (String[] args){
        Test t = new Test();//抛出异常，没人解决
        try{
            String des = t.testException();
        }catch(Exception e){
            
        }
    }
    public Test () throws Exception {
        String str = "abc";
        str.charAt(10);
    }
    public String testException () {
        try {
            System.out.println("代码执行开始");
            String str = null;
            str.length();//此处发生异常，下面不会执行
            System.out.println("try执行完");
        }catch(Exception e){
            System.out.println("捕获异常");
        }finally {
            System.out.println("我总会执行");
            return "haha";
        }
    }
}
```

`throws`：主方法抛异常没有意义，抛给虚拟机，没有方法处理异常

1）异常只能在方法上抛出，属性是不能处理异常的

2）可以抛出多个异常，交给调用方法的对象处理异常

3）抛出的异常与catch类似

```java
//自定义异常，描述我们封装的代码正确使用方式
public class MyException extends Exception{
   public MyException (String msg){
       super(msg);//继承的是Exception，Exception继承了Throwable类（以前是接口，实现了Serialble接口）
   }
}
public class Test {
    public static void main (String[] args){
        Test me = new Test();
        try{
            me.testException();
        }catch(Exception e){
            e.printStackTrace();
        }
        do something...
    }
    public testExeception () throws Exception {
        String msg = "自定义异常";
       throw new MyException (msg);
    }
}
```



