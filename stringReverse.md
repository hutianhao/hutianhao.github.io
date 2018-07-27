### 字符串反转
```java

/**
* @author kevin
* hasNextLine()可以识别空格字符;
* hasNext()不可以识别字符;
*/

import java.util.Scanner;
import java.lang.*;

public class StringReverse1{
    public static void main(String[] args){
        System.out.println("请输入字符串:");
        Scanner scan = new Scanner(System.in);
        if (scan.hasNextLine()){
            String str = scan.nextLine();
            System.out.println("反转后的字符串为:" + strReverse(str));
        }
        scan.close();
        
    }
    public static String strReverse(String str){
        char[] arr = str.toCharArray();
        int length = str.length();
        for (int i=0;i<length;i++){
            arr[i] = str.charAt(length-1-i);
        }
        return new String(arr);
    }
}
```
