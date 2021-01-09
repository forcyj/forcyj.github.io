---
layout: post
title:  "Time profiler usage"
date:   2021-01-10 01:00:00 +0800
categories:  ios
---

# Why?
Time profiler可以用来分析代码执行时间，是做启动优化的必要工具。

# 原理
每隔1ms对线程的调用栈进行采样，然后用统计学的方式去做出分析。

![原理](/imgs/timeprofiler.jpg "tet")

1.虚线是1ms的采样点

2.不会抓取到所有方法。method 3没有出现在统计结果中，方法足够快时，就统计不到。但这样符合预期。

3.并不会精确统计出方法的执行时间（区分不出来是长期运行还是多次运行）。method2在第三级等于4，是出现4次调用。method1在第二级等于4，是采样到4次。


# 入口
Menu -> product -> profile -> Release build

