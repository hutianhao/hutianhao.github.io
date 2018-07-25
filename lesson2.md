### this/类变量、类方法/三大特征
###
```java
/*
this的必要性
*/
public class Test{
    public static void main(String[] args){
        Dog dog = new Dog(12,"dog");
        Person person1 = new Person(dog,12,"kevin");
        person1.showInfo();
    }
}
class Person{
    int age;
    String name;
    public Person(Dog dog,int age,String name){
        this.age = age;
        this.name = name;
        this.dog = dog;    //一个类的成员变量是引用类型
    }
    public void showInfo(){
        System.out.println("人名是:"+this.name)
    }
}
class Dog{
    int age;
    String name;
    public Dog(int age,String name){
        this.age = age;
        this.name = name;
    }
    public void showInfo(){
        System.out.println("狗的名字是:"+this.name+"狗的年龄是:"+this.age);
    }
}
```
静态变量：可以被任何一个对象访问
```java
/*用类名可以访问到静态变量
所有对象共用一个静态变量*/
public class Test{
    Child child1 = new Child(12,"kevin");
    child1.joinGame();
    Child child2 = new Child(13,"lily");
    child2.joinGame();
    Child child3 = new Child(14,"bibe");
    child3.joinGame();
    System.out.println("总共有"+child1.total+"小孩");  //此处用类名也可以访问到静态变量Child.total或者child2.total child3.total
    
}
class Child{
    int age;
    String name;
    static int total;
    public Child(int age,String name){
        this.name = name;
        this.age = age;
    }
    public void join(){
        System.out.println("加入一个人");
        total++;
    }
}
```







