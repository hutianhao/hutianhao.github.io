### java类变量、类方法
###
- 什么是类变量
1. 类变量是所有对象共享的变量
2. 任何一个类的对象去访问它时，取到的都是相同的值
3. 同样任何一个该类的对象去修改它时，修改的也是同一个变量
- 如何定义类变量
访问修饰符 static 数据类型 变量名; 

- 如何访问一个类变量  
类名.类变量名 or 对象名.类变量名

```java
/*
即使不实例化一个对象，静态代码区的代码也会被执行
*/
public class Test2{
    static int i=1;
    static{   //静态区域块会执行一次
        i++;
    }
    public Test2(){
        i++;
    }
    public static void main(String[] args){
        Demo demo1 = new Demo();
        System.out.println(demo1.i);
        
        Demo demo2 = new Demo();
        System.out.println(demo2.i);
    } 

}
```
输出  
```java
3
4
```
###
- java类方法  
1. 类方法是属于所有对象实例的
2. 类方法中不能访问非静态变量


```java
public class Test{
    public static void main(String[] args){
        Student student1 = new Student(12,"kevin",1000);
        Student student2 = new Student(13,"lily",1000);
        
        System.out.println("total fee is:"+student1.totalFee);
    }
}
class Student{
    int age;
    String name;
    int fee;
    static totalFee;
    public Student(int age,String name,int fee){
        this.age = age;
        this.name = name;
        totalFee += fee;
    }
    //这是一个静态方法[类方法]
    //所有对象共享一个方法，在一定程度上可以节省栈和内存的开销
    public static int getTotalFee(){
        return totalFee;
    }
}













