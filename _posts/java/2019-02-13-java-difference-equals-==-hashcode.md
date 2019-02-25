---
layout: post
title:  "【java】==，equals()和hashCode()的区别"
date:   2019-02-13 22:30:00 +0800
categories: java
---

# 知识点
1. 如果是原始数据类型（如int，long），使用==比较相等
2. 如果是Object对象，==比较的是对象的引用地址/句柄(存放在栈Stack内存区域中)，而equals()方法比较的是对象里面的内容，也就是Object对象引用所指向的内存区域(存放在堆Heap中)
3. ==如果是对象，比较的是JVM中的引用地址，如果是原始数据类型，那就直接比较内容，如2 == 2 (true)
4. equals()如果是Object带的方法，默认实现也是return this == obj;对比的也是对象的引用地址，也就是说如果，两个对象的引用地址相同，那么他们指向的内存区域也是相同的，所以内容是相同的；
由于String类，复写了equals方法，以下是String.equals()方法，Long，Integer等类也有复写
<pre><code>
public boolean equals(Object anObject) {
	if (this == anObject) {
        return true;//先对比两个对象的引用地址是否相同
    }
    //然后再取出String中所有的字符，一个一个进行比较
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
            }
        }
    return false;
}
</code></pre>
5. hashCode()在Object对象中的方法，默认返回对象的引用地址，如果有复写，比如String，复写了之后返回的是通过String中字符的ACSII码通过计算得出的hash值。

总结：<br>
(1)绑定。当equals方法被重写时，通常有必要重写 hashCode 方法，以维护 hashCode 方法的常规协定，该协定声明相等对象必须具有相等的哈希码。

(2)绑定原因。Hashtable实现一个哈希表，为了成功地在哈希表中存储和检索对象，用作键的对象必须实现 hashCode 方法和 equals 方法。同(1)，必须保证equals相等的对象，hashCode 也相等。因为哈希表通过hashCode检索对象。

(3)默认。

　　==默认比较对象在JVM中的地址。

　　hashCode 默认返回对象在JVM中的存储地址。

　　equal比较对象，默认也是比较对象在JVM中的地址，同==

# 参考：
- [java中的==、equals()、hashCode()源码分析](http://www.cnblogs.com/pop822/p/6215040.html)

# 测试代码
<pre><code>
  /**
    * @see 《Java编程思想第四版》3.1.5 关系运算符
    */
  private static void test1() {
      Integer n1 = new Integer(47);
      Integer n2 = new Integer(47);
      //==比较的是两个对象的引用地址，而不是内容
      //equals()比较的是对象的内容
      System.out.println(n1 == n2);//false
      System.out.println(n1 != n2);//true
      System.out.println(n1.equals(n2));//true

      //由于a和b是原始（或称主类型）数据类型，==比较的是内容
      int a = 2;
      int b = 2;
      int c = 3;
      System.out.println(a == b);//true
      System.out.println(a == c);//false
  }
</code></pre>

<pre><code>
/**
     * String的比较
     */
    private static void strTest() {
        //由于Java将字符串存放在常量池中，所以s1和s2所指向的内存区域是同一个，
        // 即Java为"Hello"只分配了一个内存空间
        String s1 = "Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456Hello123456";
        String s2 = "Hello";
        String s3 = "Hello";
        String s4 = new String("Hello");

        //s1.hashCode() = 69609650
        //s2.hashCode() = 69609650
        //s3.hashCode() = 69609650
        //
        System.out.println("s1.hashCode() = " + s1.hashCode());
        System.out.println("s2.hashCode() = " + s2.hashCode());
        System.out.println("s3.hashCode() = " + s3.hashCode());
        System.out.println("s4.hashCode() = " + s4.hashCode());
        System.out.println(s2 == s3);//true
        System.out.println(s2.equals(s3));//true
        System.out.println(s2 == s4);//false
        System.out.println(s2.equals(s4));//true
    }
</code></pre>
