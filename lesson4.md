### java的三大特征
###
- 抽象：定义一个类的时候，就是把一类事物共有的属性和行为提取出来，形成一个模板
- 封装：就是把抽象出来的数据和对<font color=red>数据的操作</font>封装在一起，数据被保护在内部  
程序的其他部分调用被授权的方法才能对数据进行操作
public 公有的
private 私有的

- 继承：
- 多态
访问控制修饰符
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
//通过一个成员方法来控制和访问私有属性
    public float getSalary(){
        return this.salary;
    }	
}
```







