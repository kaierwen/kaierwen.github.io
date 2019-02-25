---
layout: post
title:  "【java】运算符&操作符"
date:   2019-02-15 10:00:00 +0800
categories: java
---

位运算符[参考](https://www.cnblogs.com/liaopeng/p/8436155.html)

位运算符|说明|代码示例|应用场景
:-:|:-:|:-:
^|亦或运算，针对二进制，相同的为0，不同的为1|2^3 = 1<br> 二进制表示：0010^0011 = 0001<br><br>0001 1110 ^ 0001 0100 = 0000 1010（20^30=10）<br><code>System.out.println("20^30 = " + (20 ^ 30));//10</code>
&|AND与运算，针对二进制，只要有一个为0，就为0|0001 1110 & 0001 0100 = 0001 0100（20&30=20）
\||OR或运算，针对二进制，只要有一个为1，就为1|0001 1110 & 0001 0100 = 0001 1110（20\|30=30）
\<\<|有符号（包括符号位）左移|0001 1110 << 2 == 0111 1000<br>（20 << 2 == 80）== 20*2^2 == 80
\>\>|有符号（包括符号位）左移|0001 1110 >> 2 == 0000 0111<br>（20 >> 2 == 5）== 20/2^2 == 5|
\>\>\>|无符号（忽略符号位）右移，在左端补k个0（直接操作的是内存，这个也就是操作的是补码）[参考](https://blog.csdn.net/qq_30137611/article/details/69806555)|<code>int i = -1;<br>System.out.println(i>>>24);</code><br><br>1111 1111 1111 1111 1111 1111 1111 1111 —> 逻辑右移24下，把整体往右移24次（每次一位），左边的补0 —>0000 0000 0000 0000 0000 0000 1111 1111 —>这个补码为正数，正数的补码等于其原码，也就代表了255 [参考](https://blog.csdn.net/qq_30137611/article/details/69806555)|<code>java 8 HashMap源码：static final int hash(Object key) {int h; return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);}</code>。<br><br>openjdk-jdk7u HashMap[源码](https://github.com/openjdk-mirror/jdk7u-jdk/blob/master/src/share/classes/java/util/HashMap.java)：<```static int hash(int h) {// This function ensures that hashCodes that differ only by// constant multiples at each bit position have a bounded// number of collisions (approximately 8 at default load factor).h ^= (h >>> 20) ^ (h >>> 12);return h ^ (h >>> 7) ^ (h >>> 4);}```>


# 二进制源码，反码和补码，模
参考：[补码百度百科](https://baike.baidu.com/item/%E8%A1%A5%E7%A0%81)

在计算机系统中，数值一律用补码来表示和存储。原因在于，使用补码，可以将符号位和数值域统一处理；同时，加法和减法也可以统一处理。此外，补码与原码相互转换，其运算过程是相同的，不需要额外的硬件电路。

# 参考：
