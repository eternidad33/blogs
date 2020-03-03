### 数组
int数组初始化默认为0  
必须实例化数组才能使用数组下标  
foreach循环可以避免使用下标，
foreach遍历二维数组

```java
int data[][] = new int[][]{{1, 2, 3, 4, 5}, {6, 7, 8, 9, 10}, {11, 12, 13, 14, 15}};
for (int temp[] : data) {
    for (int num : temp) {
        System.out.print(num + ",");
    }
    System.out.println();
}
```
返回数组的方法  
```java
public static int[] initArray(){
    int arr[]=new int[]{1,2,3,4,5};
    return arr;
}
```
将数组封装成一个组件  
```java
class ArrayUtil{
    public int getSum() {
        return sum;
    }

    public double getAvg() {
        return avg;
    }

    public int getMin() {
        return min;
    }

    public int getMax() {
        return max;
    }

    private int sum;
    private double avg;
    private int min;
    private int max;
    public ArrayUtil(int[] data){
        this.sum=0;
        this.max=data[0];
        this.min=data[0];
        for(int num:data){
            this.sum+=num;
            if(num>this.max)
                this.max=num;
            if(num<this.min)
                this.min=num;
        }
        this.avg=this.sum/data.length;
    }
}
```

数组快速排序  
```java
public static int[] sort(int data[]){
        for (int i = 0; i < data.length; i++) {
            for (int j = 0; j < data.length - i - 1; j++) {
                if(data[j]>data[j+1]){
                    int temp=data[j];
                    data[j]=data[j+1];
                    data[j+1]=temp;
                }
            }
        }
        return data;
    }
```
数组逆序
````java
public static int[] reverse(int data[]){
    int head=0;
    int tail=data.length-1;
    for(int i=0;i<data.length/2;i++){
        int temp=data[head];
        data[head]=data[tail];
        data[tail]=temp;
        head++;
        tail--;
    }
    return data;
}
````
数组相关的类库  
数组排序可以这样写`java.util.Arrays.sort(data);`  
系统自带的数组拷贝
```java
public static void main(String[] args) {
    int dataA[]=new int[]{1,2,3,4,5,6,7,8,9};
    int dataB[]=new int[]{11,22,33,44,55,66,77,88,99};
    System.arraycopy(dataA,5,dataB,5,3);
    printArray(dataB);
    System.out.println();
    printArray(dataA);
}
```
运行结果：
```
11,22,33,44,55,6,7,8,99,
1,2,3,4,5,6,7,8,9,
```

`System.arraycopy(dataA,5,dataB,5,3);`是将数组dataA中从索引为5，长度为3的一段数组复制到dataB中索引位置为5的地方，并替换掉相应长度
可变参数
```java
class ArrayUtil{
    public static int sum(int ... data){
        int sum=0;
        for(int temp:data){
            sum+=temp;
        }
        return sum;
    }
}
public class ArrayDemo {
    public static void main(String[] args) {
        System.out.println(ArrayUtil.sum(1,2,3));
        System.out.println(ArrayUtil.sum(new int[]{1,2,3}));
    }
}
```
在方法参数列表中`...`表示可变参数  
可变参数的作用在于，在以后进行一些程序设计或者开发者调用的时候，利用此种形式可以避免数组的传递操作
对象数组定义格式如下：
- 动态初始化：`类 对象数组名称[]=new 类[长度]`，每一个元素的内容都是null
- 静态初始化：`类 对象数组名称[]=new 类[]{实例化对象，实例化对象，实例化对象...}`

---
#### Wallpaper 每日壁纸分享
![Shadowverse.png](https://upload-images.jianshu.io/upload_images/18780226-dccb6a80fde0cf67.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

标题：**With the Fairies Shadowverse（Fanart）**   
创作者：**Dream「幽夢」**
