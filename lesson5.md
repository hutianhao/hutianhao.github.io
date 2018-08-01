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





