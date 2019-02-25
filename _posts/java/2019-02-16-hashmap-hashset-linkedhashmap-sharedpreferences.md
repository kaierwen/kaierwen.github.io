---
layout: post
title:  "【java】HashMap，HashSet，LinkedHashMap，【Android SharedPreferences】"
date:   2019-02-16 10:00:00 +0800
categories: java
---

# HashMap
- [源码分析](https://www.cnblogs.com/skywang12345/p/3310835.html)
- [面试常问的hashcode](https://www.youtube.com/watch?v=Nr56SlbMed4&list=PL3NrzZBjk6m8rEJ4O6Kpk_i1Ah8Le5Od-&index=8)

# SharedPreferences
从[源码](https://android.googlesource.com/platform/frameworks/base/+/refs/heads/master/core/java/android/content/SharedPreferences.java)可以看出，SharedPreferences采用的是Java的Map和Set实现，
```import java.util.Map;
import java.util.Set;```
