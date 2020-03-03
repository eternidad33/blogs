### 继承
`public class object.Student extends object.Person`Student类继承Person所有共有的属性和方法 
```java
import object.Person;public class Student extends Person{
    private String school;

    public String getSchool() {
        return school;
    }

    public void setSchool(String school) {
        this.school = school;
    }

    public static void main(String[] args) {
        object.Student stu=new object.Student();
        stu.setName("小明");
        stu.setAge(15);
        stu.setSchool("河北大学");
        System.out.println("姓名："+stu.getName()+",年龄："+stu.getAge()+"，学校："+stu.getSchool());
    }
}
```
子类被实例化时先调用父类的构造方法
```java
public object.Person(){
    System.out.println("【object.Person】被实例化");
}
public object.Student(){
    super();//调用父类的构造方法，写与不写都一样
    System.out.println("【object.Student】被实例化");
}
```
super(...)必须放在首行，this(...)也必须放在首行，所以两者不可同时出现
```java
    public object.Student(String name,int age ,String school){
        super(name,age);
        this.school=school;
    }
    public static void main(String[] args) {
        object.Student stu=new object.Student("小明",15,"河北大学");
        System.out.println("姓名："+stu.getName()+"，年龄："+stu.getAge()+"，学校："+stu.getSchool());
    }
```
多层继承

理论上层数最多不能超过三层
```java
class A{}
class B extends A{}
class C extends B{}
```
- 父类的私有方法不存在覆写
- 子类调用有父类覆写的方法要加super

|            Overloading             |               Override               |
| :--------------------------------: | :----------------------------------: |
|                重载                |                 覆写                 |
| 方法名称相同，参数的类型及个数不同 | 方法名称，参数类型及个数，返回值相同 |
|            没有权限限制            |  被覆写方法不能拥有更严格的控制权限  |
|           发生在一个类中           |          发生在继承关系类中          |

> 在程序类中使用this表示先从本类查找所需要的的属性或方法，如果本类中不存在则查找父类定义，如果使用super则不查找子类，直接查找父类

fanal代表不能被覆写的方法，常量

### Annotation注解

@Override 准确覆写  
@Deprecated 代表过时的类或方法  
@SuppressWarnings 压制警告  
```java
class Channel{
    public void Connect(){
        System.out.println("============Channel================");
    }
}
class DatabaseChannel extends Channel{
    @Override
    public void Connect() {
        System.out.println("=========DatabaseChannel============");
    }
}

public class JavaDemo {
    @SuppressWarnings({"deprecated"})
    public static void main(String[] args) {
        DatabaseChannel dba=new DatabaseChannel();
        dba.Connect();
    }
}
```
### 多态
向上转型`base f = new son()`可以调用父类的方法和子类中重写父类的方法

向下转型`son1 s=(son)f`不安全

instanceof 

instanceof为了保证向下转型的正确性，用于在转型之前进行判断，判断某个实例是否是某个类的对象

```java
base f = new son1();  //向上转型
f.print(); //打印我是子类
if (f instanceof son1) {
    son1 s = (son1) f;//向下转型
    s.print1();
}
```

### Object类

Object类是所有类型的父类，所以Object类可以接收所有子类的对象

`toString()`是Object自带的方法，所有继承类都可以使用

```java
A a=new A();
System.out.println(a);
System.out.println(a.toString());
```
1. 对象比较equals()
2. 判断对象是否为null
3. 判断是不是同一地址
4. 判断obj是否转换为person
5. 判断内容是否相同
```java
    public boolean equals(Object obj) {
        if (obj == null) {//判断对象是否为null
            return false;
        }
        if (this == obj) {//判断是不是同一地址
            return true;
        }
        if (!(obj instanceof person)) {//判断obj是否转换为person
            return false;
        }
        person per = (person) obj;
        return this.name.equals(per.name) && this.age == this.age;
    }
```

---
#### Wallpaper 每日壁纸分享
![Fantasy World.png](https://upload-images.jianshu.io/upload_images/18780226-b67e9b2461a095a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


标题：**Fantasy World**   
创作者：**Mrs.Venus**