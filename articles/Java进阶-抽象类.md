### 抽象类

抽象方法所在的类必须为抽象类，抽象类必须用`abstract`关键字来定义

抽象类就是在普通类上追加了抽象方法

抽象类是无法被实例化的

1. 抽象类必须提供子类
2. 抽象类的子类（非抽象类）一定要覆写抽象类中的全部抽象方法
3. 抽象类的对象实例化可以通过子类向上转型的方式完成

```java
abstract class Message{
    private String type;
    public abstract String getInfo();

    public String getType() {
        return type;
    }

    public void setType(String type) {
        this.type = type;
    }
}
class DatabaseMessage extends Message{

    @Override
    public String getInfo() {
        return "数据库连接信息";
    }
}
public class JavaDemo {
    public static void main(String[] args) {
        Message msg=new DatabaseMessage();
        System.out.println(msg.getInfo());
    }

}

```

> 抽象类自己无法直接实例化

`final`不允许有子类，`abstract`必须有子类
```java
abstract class Action{
    public static final int EAT=1;
    public static final int WORK=3;
    public static final int SLEEP=5;
    public void command(int code){
        switch (code){
            case EAT:{
                this.eat();
                break;
            }
            case SLEEP:{
                this.sleep();
                break;
            }
            case WORK:{
                this.work();
                break;
            }
            case EAT+SLEEP+WORK:{
                this.eat();
                this.work();
                this.sleep();
                break;
            }
        }
    }
    public abstract void eat();
    public abstract void sleep();
    public abstract void work();
}
```
> 抽象类中可以使用普通方法调用抽象方法

### 包装类
`Int temp = new Int(10);`装箱，将基本数据类型保存在包装类中

`int x = temp.intValue();`拆箱，从包装类中获取基本数据类型

1. 对象型的包装类，Boolen,Character
2. 数值型的包装类,Byte,Short,Integer,Long,Float,Double

基本的装箱与拆箱操作

```java
Integer obj=new Integer(10);//装箱
int x=obj.intValue();//拆箱
System.out.println(x*x);
Double d=new Double(10.1);
double num=d.doubleValue();
System.out.println(num);
Boolean b=new Boolean(false);
boolean bb=b.booleanValue();
System.out.println(bb);
```
jdk1.5之后可以实现自动装箱与拆箱操作，包装类可以直接参与数学运算
```java
Integer i=10;
i++;
System.out.println(i);//11
```

---
#### Wallpaper 每日壁纸分享
![Fantasy World](https://upload-images.jianshu.io/upload_images/18780226-ec98b0b81d1328bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

标题：**Fantasy World**   
创作者：**Mrs.Venus**


