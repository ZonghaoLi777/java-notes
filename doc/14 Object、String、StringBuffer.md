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

  