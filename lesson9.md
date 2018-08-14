### 接口的继承
- java是单继承
- 单继承机制，一个类只能继承一个父类
- 实现接口可以看做是对单继承的一种补充
- 继承是层级式的，不太灵活，这种结构修改某个类就会打破平衡
- 实现接口可以在不打破继承关系的前提下对某个类的功能进行扩展
```java

public class Test1 {

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
