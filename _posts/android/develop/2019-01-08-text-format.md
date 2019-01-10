---
layout: post
title:  "Android 文本格式化"
date:   2019-01-08 11:36:00 +0800
categories: android
---

# DecimalFormat
- 保留X位小数，如果后面不足X位小数，自动补0，如两位：（0->0.00) (1.2->1.20）
```
DecimalFormat format = new DecimalFormat("0.00");
```
- 自动去小数点后的0，如：(1->1) （1.20->1.2）（1.33->1.33）
```
DecimalFormat format = new DecimalFormat("#.##");
```
