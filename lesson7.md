### java多态
```java
public class Demo {
    public static void main(String[] args) {
        Cat cat = new Cat();
        cat.cry();
        Dog dog = new Dog();
        dog.cry();
		
        Animal an = new Cat();//让一个动物的引用指向一个猫的实例
        an.cry();
        an = new Dog();//动物的引用指向狗这个实例
        an.cry();
    }
}
class Animal{
    private String name;
    private int age;
	
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }

    public void cry() {
        System.out.println("不知道怎么叫");
    }
}

class Cat extends Animal{
    public void cry() {
    System.out.println("猫在叫");
    }
}

class Dog extends Animal{
    public void cry() {
    System.out.println("狗在叫");
    }
}
```


