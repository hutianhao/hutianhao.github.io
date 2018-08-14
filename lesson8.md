### 抽象类与接口
1. 为什么有抽象类
- 父类方法存在的不确定性，当父类的一些方法不能确定的时候可以用abstract关键词来修饰这个方法，这个方法就被称为抽象方法，这个类就被称为抽象类
2. 抽象类
- 用abstract修饰的一个类就是抽象类
- 用abstract修饰的一个方法为抽象方法
- 抽象方法不能实现 abstract void cry();
- 抽象方法在编程中用的不是很多，但是面试时候问的多
3. 抽象类注意事项
- 抽象类不能被实例化
- 抽象类不一定包含abstract方法
- 一旦一个类包含了abstract的抽象方法，这个类必须声明为抽象类
- 抽象类不能有主体

```java
/**
 * @author kevin
 * 功能：抽象类的必要性
 */
public class Test1 {
    public static void main(String[] args) {
    }
}
//这就是一个抽象类
abstract class DongWu{
    String name;
    int age;
    //动物会叫
    abstract public void cry();
}
//当一个类继承的父类是抽象类的话
//需要把抽象类中的所有抽象方法全部实现
class Mao extends DongWu{
    public void cry() {
        //do nothing...也是实现了抽象类
        System.out.println("喵喵叫");
    }
}
```
