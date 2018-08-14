### 打印一个金字塔
```java
package com.kevin;

public class Pyramid {
    public static void main(String[] args) {
        int length = 5;
        for(int i=1;i<=length;i++) {
            for(int j=1;j<=length-i;j++) {
                System.out.print(" ");
            }
        for(int k=0;k<i*2-1;k++) {
            System.out.print("*");
        }
        System.out.println();
        }
    }
}
```
