# JavaUsefulClasses
Java常用类
## 常用的类有哪些：
1。String相关的类：String类与操作他的常用方法，StringBuffer，StringBuilder

2。JDK8之前的时间API：System静态方法，Date类，Calendar类，SimpleDateFormat类

3。JDK8中新的时间API：LocalDate，LocalTime，LocalDateTime，Instant，DateTimeFormatter，其他

4。Java比较器：Comparable，Comparator接口【相当于swift中的hashable】

5。System类

6。Math类

7。BigInteger与BigDecimal
##字符串
###**概览：**

1。String是一个Final类，不可以被继承。

2。String实现了Serializable接口：表示字符串是支持序列化的。

3。实现了Comparable接口：String可以你比较大小。

4。定义了一个`final char[] value`用于储存字符串数据。

5。String是不可变的。当你声明之后，便不能修改了。_**#4**_

6。通过字面量的方式（区别与new）给一个字符串赋值，此时的字符串常量池中。

7。字符串常量池中是不会储存相同的字符串的。

8。创建的变量使用同一个字符串，仅仅是传递字符串的地址。

9。修改了原有的字符串，字符串的地址会发生改变。

10。String可以更改其中的字符，使用`.replace(oldChar: ,newChar: )`来进行赋值。

11。通过`new`来声明字符串时，相当于在常量池中创建了值，并在堆空间中创建了指向常量池中地址的dictionary，两个通过`new`关键字声明的String类型的变量，其地址值是不一样的。

    String s1 = "asd" + "qwe";
    String s2 = "asdqwe";
    String s3 = "asd";
    String s4 = "qwe";
    String s5 = s3 + "qwe";
    String s6 = "asd" + s4;
    String s7 = s3 + s4;
其中字符串直接相连的与字符串做相连运算的，存在在常量池中，地址值一致：`String s1 = "asd" + "qwe"`与`String s2 = "asdqwe"`

变量名与字符串相连或变量名与变量名相连的，存在与堆中，地址值不同：
`String s5 = s3 + "qwe"`  
`String s6 = "asd" + s4`
`String s7 = s3 + s4`

12。调用常量池中的值：`.intern()`

###**常用方法：**
####基础方法：
我们先创建一个字符串用于演示

    String string = "helloworld";
返回字符串长度

    int stringLength = string.length();
定位到string中固定的索引元素

    string.charAt(index: int);
返回字符串是否为空

    string.isEmpty();
转换成小写

    string.toLowerCase();
转换成大写

    string.toUpperCase();
去除String前后的空格

    string.trim();
是否相等

    string.equals(Sring: anotherString);
忽略大小写的情况下是否相等

    string.equalsIgnoreCase(String: anotherString);
比较大小，用于排序

    string.compareTo(String: anotherString);
取出字符串中的固定位置的字符串，是个左闭右开的区间

    string.substring(beginIndex:, endIndex:);
####检验方法：
检验字符串是否以某后缀名结束

    string.endsWith(String: Suffix);
以某字符串开始 

    string.startsWith(String: prefix);
验证以某指定索引的子字符串是否是以某字符串开始的

    string.startsWith(String: prefix, int: toffset);