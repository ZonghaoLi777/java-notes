# Objcet
Object类是Java语言中的根类，即所有类的父类。它中描述的所有方法子类都可以使用。所有类在创建对象的时候，最终找的父类就是Object。 
## equals 方法
![text](img/doc1401.png?raw=true)  
equals方法，用于比较两个对象是否相同，它其实就是使用两个对象的内存地址在比较。Object类中的equals方法内部使用的就是==比较运算符。  
在开发中要比较两个对象是否相同，经常会根据对象中的属性值进行比较，也就是在开发经常需要子类重写equals方法根据对象的属性值进行比较。如下代码演示:  
```java
class Person extends Object {
  int age;
//复写父类的equals方法，实现自己的比较方式
  public boolean equals(Object obj) {
    //判断当前调用equals方法的对象和传递进来的对象是否是同一个
    if(this == obj){
      return true;
    }
    //判断传递进来的对象是否是Person类型
    if(!(obj instanceof Person)){
      return false;
    }
    //将obj向下转型为Perosn引用，访问其属性
    Person p = (Person)obj;
    return this.age == p.age;
  }
}
```  
注意：在复写Object中的equals方法时，一定要注意public boolean equals(Object obj)的参数是Object类型，在调用对象的属性时，一定要进行类型转换，在转换之前必须进行类型判断。  
## toString方法
![text](img/doc1402.png?raw=true)  
toString方法返回该对象的字符串表示，其实该字符串内容就是对象的类型+@+内存地址值。  
由于toString方法返回的结果是内存地址，而在开发中，经常需要按照对象的属性得到相应的字符串表现形式，因此也需要重写它。  
```java
class Person extends Object{
	int age ;
	//根据Person类的属性重写toString方法
	public String toString() {
		return "Person [age=" + age + "]";
	}
}
```
# String
查阅API中的String类的描述，发现String 类代表字符串。Java 程序中的所有字符串字面值（如 "abc" ）都作为此类的实例实现。  
```java
// 演示字符串
String str = "scaler";
str = "李宗豪"
```
继续查阅API发现说字符串是常量；它们的值在创建之后不能更改，这是什么意思呢？其实就是说一旦这个字符串确定了，那么就会在内存区域中就生成了这个字符串。字符串本身不能改变，但str变量中记录的地址值是可以改变的。  
继续查API发现，字符串有大量的重载的构造方法。通过String类的构造方法可以完成字符串对象的创建，那么，通过使用双引号的方式创建对象与new的方式创建对象，有什么不同呢？看如下程序与图解：  
```java
String s3 = "abc";
String s4 = new String("abc");
System.out.println(s3==s4);//false
System.out.println(s3.equals(s4));//true,
//因为String重写了equals方法，建立了字符串自己的判断相同的依据（通过字符串对象中的字符来判断）
```
s3和s4的创建方式有什么不同呢？  
* s3创建，在内存中只有一个对象。这个对象在字符串常量池中
* s4创建，在内存中有两个对象。一个new的对象在堆中，一个字符串本身对象，在字符串常量池中  
## String类构造方法
构造方法是用来完成String对象的创建，下图中给出了一部分构造方法需要在API中找到，并能够使用下列构造方法创建对象。  
![text](img/doc1403.png?raw=true)  
```java
String s1 = new String(); //创建String对象，字符串中没有内容
byte[] bys = new byte[]{97,98,99,100};
String s2 = new String(bys); // 创建String对象，把数组元素作为字符串的内容
String s3 = new String(bys, 1, 3); //创建String对象，把一部分数组元素作为字符串的内容，参数offset为数组元素的起始索引位置，参数length为要几个元素

char[] chs = new char[]{’a’,’b’,’c’,’d’,’e’};
String s4 = new String(chs); //创建String对象，把数组元素作为字符串的内容
String s5 = new String(chs, 0, 3);//创建String对象，把一部分数组元素作为字符串的内容，参数offset为数组元素的起始索引位置，参数count为要几个元素

String s6 = new String(“abc”); //创建String对象，字符串内容为abc
```
## String类的方法查找
String类中有很多的常用的方法，我们在学习一个类的时候，不要盲目的把所有的方法尝试去使用一遍，这时我们应该根据这个对象的特点分析这个对象应该具备那些功能，这样大家应用起来更方便。  
字符串是一个对象，那么它的方法必然是围绕操作这个对象的数据而定义的。我们想想字符串中有哪些功能呢？  
* 字符串中有多少个字符?    
![text](img/doc1404.png?raw=true)    
```java
String str = "abcde";
int len = str.length();
System.out.println("len="+len);
```
* 获取部分字符串  
![text](img/doc1405.png?raw=true)   
```java
String str = "abcde";
String s1 = str.substring(1); //返回一个新字符串，内容为指定位置开始到字符串末尾的所有字符
String s2 = str.substring(2, 4);//返回一个新字符串，内容为指定位置开始到指定位置结束所有字符
System.out.println("str="+str);
System.out.println("s1="+s1);
System.out.println("s2="+s2);
```
## String类中方法查找练习
* 字符串是否以指定字符串开头。结尾同理  
![text](img/doc1406.png?raw=true)  
```java
String str = "StringDemo.java";
boolean b1 = str.startsWith("Demo");//判断是否以给定字符串开头
boolean b2 = str.startsWith("String");
boolean b3 = str.endsWith("java");//判断是否以给定字符串结尾
```
* 字符串中是否包含另一个字符串。  
![text](img/doc1407.png?raw=true)  
```java
String str = "abcde";
int index = str.indexOf(“bcd”); //判断是否包含指定字符串，包含则返回第一次出现该字符串的索引，不包含则返回-1
boolean b2 = str.contains("bcd");//判断是否包含指定字符串，包含返回true，不包含返回false
```
* 字符串中是否包含另一个字符串。  
![text](img/doc1408.png?raw=true)  
```java
String str = "abcde";
char[] chs = str.toCharArray();
byte[] bytes = str.getBytes();
```
* 判断两个字符串中的内容是否相同  
![text](img/doc1409.png?raw=true)  
```java
String str = "abcde";
String str2 = "abcde";
String str3 = "hello";
boolean b1 = str.equals(str2);
boolean b2 = str.equals(str3);
```
* 获取该字符串对象中的内容  
![text](img/doc1410.png?raw=true)  
```java
String str = new String("hello");
System.out.println( str.toString() );
System.out.pintln( str );
```
# 字符缓冲区
查阅StringBuffer的API，StringBuffer又称为可变字符序列，它是一个类似于 String 的字符串缓冲区，通过某些方法调用可以改变该序列的长度和内容。  
原来StringBuffer是个字符串的缓冲区，即就是它是一个容器，容器中可以装很多字符串。并且能够对其中的字符串进行各种操作。  
## StringBuffer的方法使用
![text](img/doc1411.png?raw=true)  
代码演示：  
```java
// 创建一个字符串缓冲区对象。用于存储数据。
StringBuffer sb = new StringBuffer();
sb.append("haha"); //添加字符串
sb.insert(2, "it");//在指定位置插入
sb.delete(1, 4);//删除
sb.replace(1, 4, "cast");//替换指定范围内的内容
String str = sb.toString();
```
注意：append、delete、insert、replace、reverse方法调用后，返回值都是当前对象自己，所以说，StringBuffer它可以改变字符序列的长度和内容。  
## 对象的方法链式调用
在我们开发中，会遇到调用一个方法后，返回一个对象的情况。然后使用返回的对象继续调用方法。这种时候，我们就可以把代码现在一起，如append方法一样，代码如下：  
```java
// 创建一个字符串缓冲区对象。用于存储数据。
StringBuffer sb = new StringBuffer();
// 添加数据。不断的添加数据后，要对缓冲区的最后的数据进行操作，必须转成字符串才可以。
String str = sb.append(true).append("hehe").toString();
```
## StringBuilder类
查阅API发现还有一个StringBuilder类，它也是字符串缓冲区，StringBuilder与它和StringBuffer的有什么不同呢？  
我们阅读StringBuilder的API说明发现，它也是一个可变的字符序列。此类提供一个与 StringBuffer 兼容的 API，但不保证同步。该类被设计用作 StringBuffer 的一个简易替换，用在字符串缓冲区被单个线程使用的时候（这种情况很普遍）。如果可能，建议优先采用该类，因为在大多数实现中，它比 StringBuffer 要快。  
# 总结
* Object: 它是所有类的超类，祖宗类。java中所有的类都直接或间接的继承这个类
  + 方法
    - public String toString() 返回当前对象中的内容, 对于Object类默认操作来说，返回的对象的类型+@+内存地址值
    - public boolean equals(Object obj) 比较两个对象内容是否相同，对于Object类默认操作来说,比较的是地址值

* String: 字符串类，字符串是常量；它们的值在创建之后不能更改
  + 方法
    - boolean equals(Object obj) 判断两个字符串中的内容是否相同
    - boolean equalsIgnoreCase(String str)  判断两个字符串中的内容是否相同, 忽略大小写
    - boolean contains(String str) 判断该字符串中 是否包含给定的字符串
    - boolean startsWith(String str) 判断该字符串 是否以给定的字符串开头
    - boolean endsWith(String str) 判断该字符串 是否以给定的字符串结尾
    - boolean isEmpty() 判断该字符串的内容是否为空的字符串  ""
    - int length() 获取该字符串的长度
    - char charAt(int index) 获取该字符串中指定位置上的字符 
    - String substring(int start) 从指定位置开始，到末尾结束，截取该字符串，返回新字符串
    - String substring(int start,int end) 从指定位置开始，到指定位置结束，截取该字符串，返回新字符串 
    - int indexOf(int ch ) 获取给定的字符，在该字符串中第一次出现的位置
    - int indexOf(String str) 获取给定的字符串，在该字符串中第一次出现的位置
    - int indexOf(int ch,int fromIndex) 从指定位置开始，获取给定的字符，在该字符
    - byte[] getBytes() 把该字符串 转换成 字节数组
    - char[] toCharArray() 把该字符串 转换成 字符数组
    - String replace(char old,char new) 在该字符串中，将给定的旧字符，用新字符替换
    - String replace(String old,String new) 在该字符串中， 将给定的旧字符串，用新字符串替换
    - String trim() 去除字符串两端空格，中间的不会去除，返回一个新字符串
    - String toLowerCase() 把该字符串转换成 小写字符串 
    - String toUpperCase() 把该字符串转换成 大写字符串
    - int indexOf(String str,int fromIndex) 从指定位置开始，获取给定的字符串，在该字符串中第一次出现的位置
* StringBuffer/StringBuilder:
  + 方法
    - public StringBuffer append(String str) 在原有字符串缓冲区内容基础上，在末尾追加新数据
    - public StringBuffer insert(int offset,String str) 在原有字符串缓冲区内容基础上，在指定位置插入新数据
    - public StringBuffer deleteCharAt(int index) 在原有字符串缓冲区内容基础上，删除指定位置上的字符
    - public StringBuffer delete(int start,int end) 在原有字符串缓冲区内容基础上，删除指定范围内的多个字符
    - public StringBuffer replace(int start,int end,String str)在原有字符串缓冲区内容基础上，将指定范围内的多个字符 用给定的字符串替换
    - public StringBuffer reverse() 将字符串缓冲区的内容 反转  "abc"----"cba"
    - public String substring(int start) 从指定位置开始，到末尾结束，截取该字符串缓冲区，返回新字符串
    - public String substring(int start,int end)  从指定位置开始，到指定位置结束，截取该字符串缓冲区，返回新字符串