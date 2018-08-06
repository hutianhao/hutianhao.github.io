### java的三大特征：封装、继承、多态
--- 
1. 抽象：定义一个类的时候，实际上就是把一类事物共有的属性和行为提取出来，形成一个物理模型
2. 封装：把抽象出来的数据和对数据的操作封装在一起，数据被保护在内部，程序的其他部分只有通过被授权的操作（成员方法）才能对数据进行操作  
- 原则：尽可能把成员属性都做成私有的private   
- 访问控制修饰符：
1. 公开级别：用public修饰，对外公开
2. 受保护级别：用protected修饰，对子类和同一个包中的类公开
3. 默认级别：没有修饰符号，向同一个包的类公开
4. 私有级别：用private修饰，只有类本身可以访问，不对外公开  

访问级别|访问控制修饰符|同类|同包|子类|不同包
---|---|---|---|---|---
公开|public|可以|可以|可以|可以
受保护|protected|可以|可以|可以|不可以
默认|没有修饰符|可以|可以|不可以|不可以
私有|private|可以|不可以|不可以|不可以
```java
public class Test4{
    public static void main(String[] args){
        Clerk clerk = new Clerk("kevin",25,10000000f);
	System.out.println("薪水是："+ clerk.getSalary());
    }
}
class Clerk{
    public String name;
    private int age;
    private float salary;
		
    public Clerk(String name,int age,float salary){
        this.name = name;
	this.age = age;
	this.salary = salary;
    }
//通过一个成员方法来控制和访问私有属性，相当于一个接口
    public float getSalary(){
        return this.salary;
    }	
}

```
### 包
- 包名都是小写
1. 不同包下面可以创建同名的类，可以区分相同名字的类
2. 当类很多的时候，可以很好的管理包
3. 控制访问范围
- 打包命令   
1. package com.kevin;   
2. 生成的class字节码放到com.kevin中去   
3. 打包命令一般放在文件开始的地方
- 常用的包
1. java帮助文档java.applet;java.awt等等
2. java.lang.* 包，自动引入
3. java.util.* 工具包
4. java.net.* 网络开发包
5. java.awt.* 窗口工具包
- 引入包   
import java.util.*
```java
package com.kevin

public class Test{
    public static void main(String[] args){
        Dog dog = new Dog();
	System.out.println(dog.price);
    }
}
class Dog{
    public int a;
    protected String name;
    String color;
    private float price;
    
    public void ab1(){
        System.out.println(a);
    } 
}
```
```java
package com.hookie;
//Cat与test不在用一个包中，不可以直接去访问除了public以外的成员变量
public class Cat {
    public int age;
    protected String name;
    String address;
    private float price;

    public void getAge(){
        System.out.println(age);
    }
    //如果想要访问除了public以外的成员变量的话，getName打开接口
    public String getName(){
        return this.name;
    }
}
```
```java
package com.kevin;

import com.hookie.Cat;

import java.util.HashMap;

public class Test {
    public static void main(String[] args){
        Dog dog = new Dog();
        System.out.println(dog.color);
        HashMap hm = new HashMap();
        //不同包的调用，直接在上面import就可以
        Cat cat = new Cat();
        cat.getName();//访问Cat中的protected成员变量
    }
}
//已经有了一个public，不能再定义为public的限制符
class Dog{  
    public int a;
    protected String name;
    String color;
    private float price;

    public void ab1(){
        System.out.println(a);
    }
}
```
### 继承  
1. 当多个类拥有相同的属性和方法时，可以从这些类中抽象出父类，在父类中定义这些相同的属性和方法，所有的子类不需要重新定义的某些属性和方法  
2. class 子类 extends 父类  
3. public和protected修饰符的属性和方法可以被继承，父类的私有属性和方法是不能被继承的，如果不希望子类继承某个属性或方法，将其声明为私有即可
4. 子类最多继承一个父类，java中通过接口解决不能够多重继承的问题，C++中允许多重继承
5. java中所有的类都是Object的子类，java.lang.Object
6. 
```java
class Student{
    //希望被继承，不能写成private，先写成public
    public int age;
    public String name;
    public String gender;
    
    public void showName(){
        System.out.println(this.name);
    }
}
//小学生类继承Student类
class Pupil extends Student{
     public void showAge(){
        System.out.println(this.age);
    }
}
//中学生类继承Student类
class MiddleStu extends Student{
     public void showGender(){
        System.out.println(this.gender);
    }
}
```
- 例：继承JFrame类
```java
//继承JFrame类，可以生成一个对话框
package com.kevin;

import  javax.seing.*;
public class Demo extends JFrame{
    public static void main(String[] args){
        Demo demo = new Demo();
    }
    public Demo(){//定义一个构造函数
        this.setVisible(true);
	this.setSize(400,400);
    }
}
```
- 方法重载：就是累的同一种功能的多种实现方式，采用哪一种方式取决于调用者给出的参数
- 方法重载注意事项：
1. 方法名相同
2. 方法的参数类型，个数，顺序至少有一项不同
3. 如果只是定义的函数返回类型不同，不能构成重载
```java
public int getMax(int a,int b){
    return a;
}
public float getMax(int a,int b){
    return a;
}
```
4. 如果只是控制访问修饰符符号不一样能否构成重载？也不能构成重载
```java
protected int getMax(int a,int b){
    return a;
}
public int getMax(int a,int b){
    return a;
}
```

```java
public class Demo{
    public static void main(String[] args){
        
    }
}
class GetMax{
    public int getMax(int a,int b){
        if(a>b){
            return a;
        }
        else{
             return b;
	     }
    }
    public float getMax(float a,float b){
    	if(a>b){
            return a;
        }
        else{
            return b;
        }
    }
}
```
- 方法的覆盖（override）
```java
public class Demo{
    public static void main(String[] args){
        Cat cat = new Cat();
	cat.cry();
    }
}
class Animal{
    int age;
    String name;
    public void cry(){
        System.out.println("我是动物不知道怎么叫");
    }
}
class Cat extends Animal{
    //覆盖父类的方法
    public void cry(){
        System.out.println("猫猫叫");
    }
}
class Dog extends Animal{
    //覆盖父类的方法
    public void cry(){
        System.out.println("汪汪叫");
    }
}






