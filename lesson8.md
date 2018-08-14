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

### 接口  
1. 注意事项
- 一个类实现了一个接口，需要该类把这个接口的所有方法统统实现
- 接口不能被实例化
- 接口中的所有方法都不能有主体
- 抽象类是可以有实现的方法，如果声明了abstract就不能去实现 
- 但是接口中的方法一个都不能有主体
- 接口是更加抽象的抽象类
```java
/**
 * @author kevin
 * 功能：接口的讲解
 */
public class Interface {
	public static void main(String[] args) {
		Computer computer = new Computer();
		Camera camera = new Camera();
		computer.useUsb(camera);
		//Usb usb = new Usb();
		System.out.println(Usb.a);//很多人喜欢把静态变量定义在接口中
	}
}
interface A{
	public void A();
}
//一个接口可以继承一个接口
interface kkk extends A{
	public void show();
}
interface Usb{
	int a = 1;
	//开始工作
	public void start();
	//停止工作
	public void stop();
	
}
//编写照相机类，并实现Usb接口
//一个类实现了一个接口，需要该类把这个接口的所有方法统统实现
class Camera implements Usb,kkk{
	public void start() {
		System.out.println("begin with");
	}
	
	public void stop() {
		System.out.println("end with");
	}
	
	public void show() {
		System.out.println("kkk");
	}
	
	public void A() {
		
	}
}
//计算机
class Computer{
	//开始使用usb接口
	public void useUsb(Usb usb) {
		usb.start();
		usb.stop();
	}
}

```
- 接口中可以有变量
- 接口中的变量本质上是static，而且是final，不管你是否加final
- 接口是更加抽象的抽象类
- 接口体现了程序设计的多态和高内聚低耦合的设计思想






