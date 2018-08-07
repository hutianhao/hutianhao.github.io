- 方法覆盖（override）-注意事项  
子类有一个方法，和父类的某个方法的名称，返回类型，参数一样，那么我们就说子类的这个方法覆盖了父类的方法
1. 子类的方法的返回类型，参数，方法名称，要和父类的方法一样，否则编译出错
2. 子类方法不能缩小父类方法的访问权限
```java
//约瑟夫问题：  
有n个人围成一圈，编号为1,2...n,约定编号为k的人开始从1报数，数到m的那个人出列，他的下一个位又从1开始报数，数到m的那个人又出列，直到所有人出列位置，由此产生一个序列
/**
*@author kevin
*功能：丢手帕问题
*/
//首先构造环形链表
public class Demo{
    public static void main(String[] args){
        CycLink cyclink = new CycLink();
        cyclink.setLen(5);
        cyclink.setK(2);
        cyclink.setM(2);
        cyclink.createLink();
        cyclink.show();
        cyclink.play();
    }
}
class Child{
    public int num;
    Child nextChild; //引用类型
    public Child(int num){//定义一个构造方法
        //给一个编号
        this.num = num;
    }
}
//环形链表
class CycLink{
    //先定一个指向链表头的第一个小孩的引用
    //指向第一个小孩的引用不能动
    Child firstChild = null;
    Child temp;
    int len = 0; //表示共有多少个小孩
    int k = 0;
    int m = 0;
    //设置m的大小
    public void setM(int m){
        this.m = m;
    }
    //设置环形链表的大小
    public void setLen(int len){
        this.len = len;
    }
    //设置从第几个人开始数数
    public void setK(int k){
        this.k = k;
    }
    //开始play
    public void play(){
        Child temp = this.firstChild;
        //1.先找到数数的人
        for (int i=1;i<k;i++){
            temp = temp.nextChild;
        }
        
        while(this.len!=1){
        //2.数m下
        for(int j=1;j<m;j++){
            temp = temp.nextChild;
        }
        //找到要出圈的前一个小孩
        Child temp2 = temp;
        while(temp2.nextChild!=temp){
            temp2=temp2.nextChild;
        }
        //3.将数到m的小孩，退出圈
        temp2.nextChild = temp.nextChild;
        //让temp指向下一个数数的小孩
        temp = temp.nextChild;
  
        this.len--;
        }
        
        //走后一个小孩
        System.out.println("最后出圈"+temp.num);
    }
    //初始化环形链表
    public void createLink(){
        for (int i=1;i<=len;i++){
            if(i==1){
            //先创建第一个小孩
            //分别有两个指针指向第一个小孩firstChild和temp
            Child ch = new Child(i);
            this.firstChild = ch;
            this.temp = ch;
            }
            else{
                if(i == len){//创建最后一个小孩
                    Child ch = new Child(i);
                    temp.nextChild = ch;
                    temp = ch;
                    temp.nextChild = this.firstChild;
                }else{
                Child ch = new Child(i);
                temp.nextChild = ch;
                temp = ch;
                }
            }
        }
    }
    public void show(){
        Child temp = this.firstChild;
        do{
            System.out.print(temp.num);
            temp = temp.nextChild;
        }while(temp!=this.firstChild);
    } 
}
