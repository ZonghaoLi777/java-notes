# 类
  类，它是引用数据类型，与之前学习的所有引用数据类型相同，自定义类也是一种数据类型。只是自定义类型并非Java为我们预先提供好的类型，而是我们自己定义的一种引用数据类型用来描述一个事物。  
## 类的定义格式
  ```
  // 创建java文件，与类名相同
  public class 类名{
    数据类型  属性名称1；
    数据类型  属性名称2；
    …
  }
  ```  
  通过类的定义格式，来进行手机类的描述，如下所示  
  ```
  public class Phone {
    /*
    * 属性
    */
    String brand;// 品牌型号
    String color;// 颜色
    double size; // 尺寸大小
  }
  ```  
## 类的使用格式
  导包：我们将所有的类放到同一个文件夹下，可以避免导包。  
  创建对象：数据类型  变量名 = new 数据类型();  
  调用方法：目前我们定义的自定义类不涉及方法，只是属性（自定义类中的方法部分在面向对象部分讲解）  
  访问属性：变量名.属性 (这是当前的方式，后期会采取调用方法的方式替代掉直接访问的方式来完成对属性的访问。)  
# ArrayList集合
  数组可以保存多个元素，但在某些情况下无法确定到底要保存多少个元素，此时数组将不再适用，因为数组的长度不可变。  
  ArrayList集合是程序中最常见的一种集合，它属于引用数据类型（类）。在ArrayList内部封装了一个长度可变的数组，当存入的元素超过数组长度时，ArrayList会在内存中分配一个更大的数组来存储这些元素，因此可以将ArrayList集合看作一个长度可变的数组  
## 集合的创建
  创建集合的常用格式在此说明一下：  
  导包：import java.util.ArrayList;  
  创建对象：与其他普通的引用数据类型创建方式完全相同，但是要指定容器中存储的数据类型：  
  ArrayList<要存储元素的数据类型> 变量名 = new ArrayList<要存储元素的数据类型>();  
  * 集合中存储的元素，只能为<>括号中指定的数据类型元素；
  * “<要存储元素的数据类型>”中的数据类型必须是引用数据类型，不能是基本数据类型；  
  下面给出8种基本数据类型所对应的引用数据类型表示形式:  
  ![text](img/doc0601.png?raw=true)  
  * 存储String类型的元素
    + ArrayList<String> list = new ArrayList<String>();
  * 存储int类型的数据
    + ArrayList<Integer> list = new ArrayList<Integer>(); 
  * 存储Phone类型的数据
    + ArrayList<Phone> list = new ArrayList<Phone>();
## 集合中常用方法
  ![text](img/doc0602.png?raw=true)  
  强调一点，ArrayList集合相当于是一个长度可变的数组，所以访问集合中的元素也是采用索引方式访问，第一个元素存储在索引0的位置，第二个元素存储在索引1的位置，依次类推  
## 集合的遍历
  通过集合遍历，得到集合中每个元素，这是集合中最常见的操作。集合的遍历与数组的遍历很像，都是通过索引的方式  
  ```
  import java.util.ArrayList;
  public class ArrayListDemo02 {
  	public static void main(String[] args) {
  		//创建ArrayList集合
  		ArrayList<Integer> list = new ArrayList<Integer>();
  		//添加元素到集合
  		list.add(13);
  		list.add(15);
  		list.add(22);
  		list.add(29);
  		//遍历集合
  		for (int i = 0; i < list.size(); i++) {
  			//通过索引，获取到集合中每个元素
  			int n = list.get(i);
  			System.out.println(n);
  		}
  	}
  }
  ```  
## 集合中的常用方法补充
  ![text](img/doc0603.png?raw=true)  
  * boolean add（int index,  Object obj）
    + 功能：在集合中指定index位置，添加新元素obj
    + 功能说明：假设集合list中有元素[“java”,“javaEE”]，当使用add(1，“javaWeb”)后，集合list中的元素为[“java”,“javaWeb”,“JavaEE”]。
  * Object set（int index, Object obj）
    + 功能：用指定元素obj替代集合中指定index位置的元素
    + 功能说明：假设集合list中有元素[“java”,“javaEE”]，当使用set(0，“javaWeb”)后，集合list中的元素为[“javaWeb”,“JavaEE”]。
  * Object remve（int index）
    + 功能：从集合中删除指定index处的元素，返回该元素
    + 功能说明：假设集合list中有元素[“java”,“javaEE”]，当使用remove(0)后，集合list中的元素为[“JavaEE”]，返回值为“java”。
  * void clear（）
    + 功能：清空集合中所有元素
    + 功能说明：假设集合list中有元素[“java”,“javaEE”]，当使用clear()后，集合list中的元素为空[]。  
# 总结
  * 引用数据类型（类）
    + 类的类型为两种：
      - 第一种，Java为我们提供好的类，如Scanner类，Scanner类等，这些已存在的类中包含了很多的方法与属性，可供我们使用。
      - 第二种，我们自己创建的类，按照类的定义标准，可以在类中包含多个方法与属性，来供我们使用。
    + 创建类的格式
  ```
  public class 类名 {
    //可以定义属性
    //也可以定义方法
  }
  ```  
  + 使用类的格式：
    - 类名 变量名 = new 类名();
  + 使用类中的属性与方法格式
    - 使用属性： 变量名.属性
    - 使用方法： 变量名.方法()
  * ArrayList集合
    + 它属于引用数据类型（类）。我们可以看作一个长度可变的数组。
    + 创建集合的方式
      - ArrayList<要存储元素的数据类型> 变量名 = new ArrayList<要存储元素的数据类型>();
    + 集合中的常用方法
      - boolean add（Object obj）
      - Object get（int index）
      - int size（）
      - boolean add（int index,  Object obj）
      - Object set（int index, Object obj）
      - Object remve（int index）
      - void clear（）
