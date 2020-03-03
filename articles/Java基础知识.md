从当前所在路径加载类  
SET ClASSPATH=.  

PATH：是操作系统提供的路径配置，定义所有可执行程序的路径  
CLASSPATH：是由JRE提供的，用于定义Java程序解释时类加载路径CLASSPATH=路径”的命令形式来进行定义；

---
Java 1.9之后才有的Jshell

java中的关键字
![java中的关键字](https://upload-images.jianshu.io/upload_images/18780226-4f8b31bf3376649e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
int的取值范围为-2147483648到2147483647

```java
public static void main(final String args[]) {
    final int max = Integer.MAX_VALUE;
    final int min = Integer.MIN_VALUE;
    System.out.println(max); // 2147483647
    System.out.println(min); // -2147483648
    System.out.println(max + 1); // -2147483648
    System.out.println(max + 2); // -2147483647
    System.out.println(min - 1); // 2147483647
}
```

大写字母范围：A(65)~Z(90)
小写字母范围：a(97)~z(122)
数值范围：'0'(48)~'9'(57)

Java 获取变量类型
```java
public static void main(final String args[]) {
		boolean a = false;
		System.out.println(getType(a));
}
public static String getType(Object o) {
	return o.getClass().toString();
}
```
---
this关键字  
this():调用无参的构造函数  
this(name):调用参数为name的构造函数  

```java
public class Person {
    private String name;
    private int age;

    public String getName() {
        return name;
    }


    public Person(){
        System.out.println("产生新的对象");
    }
    public Person(String name){
        this();//调用无参构造
        this.name=name;
    }
    public Person(String name, int age) {
        this(name);//调用单参构造
        this.age = age;
    }
}
```
this(...)必须放在首行  
四个参数的代码简写：
```java
public class EMP {
    private long id;
    private String name;
    private String dept;
    private double salary;

    public EMP(long id, String name, String dept, double salary) {
        this.id = id;
        this.name = name;
        this.dept = dept;
        this.salary = salary;
    }

    public EMP(long id, String name, String dept){
        this(id,name,dept,0.0);
    }

    public EMP(long id, String name) {
        this(id,name,null,0.0);
    }

    public EMP(long id) {
        this(id,null,null,0.0);
    }
    //必须提供无参构造
    public EMP() {
        this(0,null,null,0.0);
    }
}
```

---
Static属性由类名直接调用  
static方法只允许调用static属性或static方法
非static方法允许调用static属性或static方法

static的定义的方法或属性都不是你代码编写之初所需要考虑的内容，只有在回避实例化对象描述公共属性的情况下才会考虑static定义的属性或者是方法

静态代码块最先执行，而且只会执行一次，用于对静态属性的初始化，构造块会优于构造方法先执行
```java
public Person(){
    System.out.println("【构造方法】：构造方法执行");
}

{
    System.out.println("【构造块】：构造块执行");
}

static {
    System.out.println("【静态代码块块】：静态代码块执行");
}

public static void main(String[] args) {
    new Person();
    new Person();
    new Person();
}
```
运行结果：  

    【静态代码块块】：静态代码块执行
    【构造块】：构造块执行
    【构造方法】：构造方法执行
    【构造块】：构造块执行
    【构造方法】：构造方法执行
    【构造块】：构造块执行
    【构造方法】：构造方法执行

---
#### Wallpaper 每日壁纸分享
![Sakura.png](https://upload-images.jianshu.io/upload_images/18780226-169c5e89b4a15077.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

标题:**Sakura[1080p]**   
创作者：**Mrs.Venus**