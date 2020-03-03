## 对象关联
```java
class Car {
    private String name;
    private double price;
    private Person per;

    public Car(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public Person getPer() {
        return per;
    }

    public void setPer(Person per) {
        this.per = per;
    }

    public static void main(String[] args) {
        Person per = new Person("张三", 15);
        Car car = new Car("BMW", 15000.00);
        car.setPer(per);
        car.getPer().tell();
    }
}
```

---

java源代码目录:C:\Program Files (x86)\Java\jdk-9\lib\src.zip

JDK 1.8及以前的String支持类

![java1.8](https://cdn.jsdelivr.net/gh/eternidad33/picbed@master/img/java1.8String.png)

JDK 1.9的String支持类

![java1.9](https://cdn.jsdelivr.net/gh/eternidad33/picbed@master/img/java1.9string.png)

JDK 1.8及以前String类保存的是字符数组

JDK 1.9及以后String类保存的是字节数组

---

## String对象的比较
直接为字符串赋值会是字符串变量指向字符串池中的内存地址  
new String()会开辟新的内存  
```java
public static void main(String[] args) {
        String A = "hellojava";
        String B = "hellojava";
        String C=new String("hellojava");
        System.out.println(A==B);//true
        System.out.println(A==C);//false
        System.out.println(A.equals(C));//true

    }
```

## 将所有小写字母转换成大写

先将字符串转换成字符数组，然后每个字符的编码-32

```java
String str = new String("hellojava");
char result[] = str.toCharArray();//将字符串转化为字符数组
for(int x=0;x<result.length;x++)
    result[x]-=32;
System.out.println(new String(result));
```

## 判断是否全为数字
先将字符串转换成字符数组，`if (result[i] < '0' || result[i] > '9')`挨个判断每个字符

```java
public static void main(String[] args) {

    String str = new String("hellojava");
    System.out.println(isNumber(str) ? "该字符串全为数字" : "该字符串不全为数字");
}

private static boolean isNumber(String str) {
    char result[] = str.toCharArray();
    for (int i = 0; i < result.length; i++) {
        if (result[i] < '0' || result[i] > '9')
            return false;
    }
    return true;
}
```

## 字符串的比较
`str.equals(str1)`区分大小写比较  
`str.equalsIgnoreCase(str1)`不区分大小写比较  
`str.compareTo(str1)`字符串的大小的比较  
`str.compareToIgnoreCase(str1)`忽略大小写的字符串大小比较
```java
public static void main(String[] args) {

    String str = new String("helloJava");
    String str1=new String("Hellojava");
    System.out.println(str.equals(str1));//区分大小写比较
    System.out.println(str.equalsIgnoreCase(str1));//不区分大小写比较
    System.out.println(str.compareTo(str1));//字符串的大小的比较，'h'-'H'
    System.out.println(str.compareToIgnoreCase(str1));//忽略大小写的字符串大小比较
    System.out.println(str1.compareTo(str));
    System.out.println(str1.compareToIgnoreCase(str));

}
```


## 字符串的查找
`str.contains("hello")`判断字符串中是否含有hello  
`str.indexOf("Java")`查询Java是否存在于str中，存在返回首字母索引位置，不存在返回-1  
`str.lastIndexOf("Java")`从后向前查询  
`str2.endsWith("com")`判断是否以com结尾  
`str2.startsWith("www")`判断是否以www开头
```java
public static void main(String[] args) {

    String str = new String("helloJava");
    System.out.println(str.contains("hello"));//判断字符串中是否含有hello
    System.out.println(str.contains("Python"));
    System.out.println(str.indexOf("Java"));//查询Java是否存在于str中，存在返回首字母索引位置，不存在返回-1
    System.out.println(str.indexOf("python"));
    System.out.println(str.lastIndexOf("Java"));//从后向前查询
    System.out.println(str.lastIndexOf('a',7));
    String str2=new String("www.baidu.com");
    System.out.println(str2.endsWith("com"));//判断是否以com结尾
    System.out.println(str2.startsWith("www"));//判断是否以www开头
    System.out.println(str2.startsWith(".",3));
}
```

## 字符串的替换
`str.replaceAll("Java", "Python")`将全部的Java替换成Python  
`str.replaceFirst("Java", "Python")`将第一个Java替换成Python
```java
String str = new String("helloJava,Java");
System.out.println(str.replaceAll("Java", "Python"));//将全部的Java替换成Python
System.out.println(str.replaceFirst("Java", "Python"));//将第一个Java替换成Python
```

## 字符串的拆分
`str.split(" ")`以空格全部拆分，返回字符串数组  
`str.split(" ",2)`以空格拆分成2个，返回字符串数组  
`str1.split("\\.")`拆不开的情况要用"\\"进行转义
```java
String str = new String("hello Java hello Java");
String[] result = str.split(" ");//以空格全部拆分，返回字符串数组
for (int i = 0; i < result.length; i++) {
    System.out.println(result[i]);
}
String[] resulta = str.split(" ",2);//以空格拆分成2个，返回字符串数组
for (int i = 0; i < resulta.length; i++) {
    System.out.println(resulta[i]);
}
String str1="127.0.0.1";
String[] re=str1.split("\\.");//拆不开的情况要用"\\"进行转义
for (int i = 0; i < re.length; i++) {
    System.out.println(re[i]);
}
```

## 字符串的截取
`str.substring(startIndex,endIndex)`截取str从startIndex到endIndex的字符串片段  
```java
String user="2020111-photo-秦始皇.png";
int startIndex=user.indexOf("-",user.indexOf("photo"))+1;
int endIndex=user.lastIndexOf(".");
System.out.println(user.substring(startIndex,endIndex));
```

## 字符串的格式化

format是一个静态方法,直接通过**String类调用**`String.format("姓名：%s，年龄：%d，分数：%5.2f",name,age,score`)
```java
String name="小明";
int age=10;
double score=59.123456789;
String str=String.format("姓名：%s，年龄：%d，分数：%5.2f",name,age,score);//format是一个静态方法
System.out.println(str);
```

## 其他字符串相关的方法
`str.concat(str2)`字符串的连接  
`str.isEmpty()`判断字符串内容是否为空  
`str.trim()`去掉字符串中所有空格  
`str.toUpperCase()`全部转换成大写  
`(str.toLowerCase()`全部转换成小写  
```java
class StringUtil{
    public static String initCap(String str){//将字符串首字母大写，其余字母小写
        if(str==null||"".equals(str))
            return str;
        return str.substring(0,1).toUpperCase()+str.substring(1).toLowerCase();
    }
}



public class StringDemo {

    public static void main(String[] args) {
        String str1 = "hello ";
        String str2 = "Java";
        String str3="";
        System.out.println(str1.concat(str2));//字符串的连接
        System.out.println(str1.isEmpty());//判断字符串内容是否为空
        System.out.println(str3.isEmpty());
        String str4="         Hello Java     ";
        String trimStr4=str4.trim();//去掉字符串中所有空格
        System.out.println(str4.length());
        System.out.println(trimStr4.length());
        System.out.println(str4);
        System.out.println(trimStr4);
        System.out.println(str1.toUpperCase());//全部转换成大写
        System.out.println(str2.toLowerCase());//全部转换成小写
        String a="aSDDasdF";
        String b="m";
        System.out.println(StringUtil.initCap(a));
        System.out.println(StringUtil.initCap(b));


    }

}
```

---
#### Wallpaper 每日壁纸分享

![Snow.png](https://upload-images.jianshu.io/upload_images/18780226-1d163154c1c2bd56.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


标题：**Snow**   
创作者：**Trinity<sup>TM</sup>**