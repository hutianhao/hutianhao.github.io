### 接口的继承
- java是单继承
- 单继承机制，一个类只能继承一个父类，可以保证类的纯洁性
- 实现接口可以看做是对单继承的一种补充
- 继承是层级式的，不太灵活，这种结构修改某个类就会打破平衡
- 实现接口可以在不打破继承关系的前提下对某个类的功能进行扩展
```java

public class Test1 {
    public static void main(String[] args){
        Monkey monkey = new Monkey();
        LittleMonkey littlemonkey = new LittleMonkey();
        
        monkey.jump();
        littlemonkey.flying();
        littlemonkey.swimming();
    }
}

interface Bird{
    public void flying();
}

interface Fish{
    public void swimming();
}

class Monkey{
    int name;
    public void jump() {
        System.out.println("monkey can jump");
    }
}

class LittleMonkey extends Monkey implements Fish,Bird{
    @Override
    public void swimming() {
        System.out.println("little monkey can swim");
    }

    @Override
    public void flying() {
        System.out.println("little monkey fly");
    }
}
```
### 实现接口和继承父类的区别
1. 实现接口可以看做是对继承的一种补充
2. 实现接口可在不打破继承关系的前提下，对某个类功能扩展，非常灵活
- 前期绑定：在程序运行之前进行绑定，由编译器和连接程序实现，又叫静态绑定，比如static方法和final方法，注意这里包括private方法，因为他是隐式final的  
如：int a = 1;
- 后期绑定：在运行的时候根据对象的类型进行绑定，由方法调用机制来实现，因此又叫动态绑定。或者运行时绑定，除了前期绑定以外的方法都是后期绑定
- 在编译时候就能确定的类型就是前期绑定，只能在运行的时候才能知道的类型就是后期绑定

```java
//用接口实现多态的案例
interface Car{
    String getName();
    int getPrice();
}
```
### final
- final可以修饰变量或者方法
1. 当不希望父类的某个方法被子类覆盖的时候@Override，可以用final关键字修饰
2. 当不希望类的某个变量的值被修改时，可以用final修饰，final修饰的变量叫常量，如果一个变量是final必须赋初值
3. 当不希望类被继承时，可以用final修饰
- 考虑final的场景
1. 因为安全的考虑，类的某个方法不允许被修改
2. 类不会被其他的类继承
3. 类的某些变量值是不能改变的，如圆周率
4. final变量在定义的时候必须赋初值

```java
//给成员方法用final来修饰，则表明不可以被修改或不可被覆盖
package com.kevin;

public class Test{
    public static void main(String[] args){
        A a = new A();
        a.show();
        B b = new B();
        b.show();
    }
}
//final修饰类则表示该类不能被继承
fianl class A{
   int a;//如果不赋初值，a为0
   //圆周率不需要别人修改
   final float rate_a_b = 3.1415926f; //final值一般都是下划线来表示
   final public void sendMessage(){
       System.out.println("send message");
   }
   public void show(){
       System.out.println("a=="+a);
   }
}
class B extends A{
    public B(){//构造函数
    	a++;
    	rate = rate +1;//这里会报错，final的成员变量不能被修改
    }
}



