# 引用数据类型
## Scanner类
  * 引用数据类型的使用
    + 与定义基本数据类型变量不同，引用数据类型的变量定义及赋值有一个相对固定的步骤或格式。
    + 数据类型  变量名  =  new 数据类型();
    + 每种引用数据类型都有其功能，我们可以调用该类型实例的功能。
    + 变量名.方法名();
  * Scanner类
    + Scanner类是引用数据类型的一种，我们可以使用该类来完成用户键盘录入，获取到录入的数据。
    + Scanner使用步骤：
      - 导包：import java.util.Scanner;
      - 创建对象实例：Scanner sc = new Scanner(System.in);
      - 调用方法：
      - int  i = sc.nextInt(); 用来接收控制台录入的数字
      - String s = sc.next(); 用来接收控制台录入的字符串
## 随机数类Random
  * 方法简介
    + public int nextInt(int maxValue)	产生[0,maxValue)范围的随机整数，包含0，不包含maxValue；
    + public double nextDouble()  产生[0,1)范围的随机小数，包含0.0，不包含1.0。
  * Random使用方式:
    + import导包：所属包java.util.Random  
    + 创建实例格式：Random 变量名 = new Random();
# 流程控制语句
  * 选择结构if  
  ```
  if (判断条件){
    执行语句1
    ……
  }
  ```  
  * if…else语句
  ```
  if (判断条件){
    执行语句1
    ……
  }else{
    执行语句2
    ……
  }
  ```  
  * if…else if…else语句  
  ```
  if (判断条件1) {
    执行语句1
  } else if (判断条件2) {
    执行语句2
  }
  ...
  else if (判断条件n) {
    执行语句n
  } else {
    执行语句n+1
  }
  ```  
  * 选择结构if语句与三元运算转换  
  判断条件 ? 表达式1 : 表达式2  
  * 循环语句while
  ```
  while(循环条件){
  执行语句
  ………
  }
  ``` 
  * 循环语句for
  ```
  for（初始化表达式; 循环条件; 操作表达式）{
    执行语句
    ………
  }
  ```  
  * 循环语句do…while
  ```
  do {
  执行语句
  ………
  } while(循环条件);
  ```  
  * 跳转语句（break、continue）
    + break语句
      - 在switch条件语句和循环语句中都可以使用break语句。当它出现在switch条件语句中时，作用是终止某个case并跳出switch结构。当它出现在循环语句中，作用是跳出循环语句，执行后面的代码。
    + 标记
      - 当break语句出现在嵌套循环中的内层循环时，它只能跳出内层循环，如果想使用break语句跳出外层循环则需要对外层循环添加标记。
  ```
  public class BreakDemo02 {
    public static void main(String[] args) {
      int i, j; // 定义两个循环变量
      itcast: for (i = 1; i <= 9; i++) { // 外层循环
        for (j = 1; j <= i; j++) { // 内层循环
          if (i > 4) { // 判断i的值是否大于4
            break itcast; // 跳出外层循环
          }
          System.out.print("*"); // 打印*
        }
        System.out.print("\n"); // 换行
      }
    }
  }
  ```  
    + continue语句
      - continue语句用在循环语句中，它的作用是终止本次循环，执行下一次循环
  * 选择结构switch
  ```
  switch (表达式){
    case 目标值1:
      执行语句1
      break;
    case 目标值2:
      执行语句2
      break;
    ．．．．．．
    case 目标值n:
      执行语句n
      break;
    default:
      执行语句n+1
      break;
  }
  ```  