---
title: OI中常犯的错误
tags:
  - 实用
abbrlink: 19193b76
date: 2019-07-24 17:04:23
---

1.对拍的时候不加$srand(time(NULL))$，对拍了好久以为自己稳了，结果成绩爆$0$。

2.这个错误比较难发现：

```cpp
#define Calc(x) 1-x
printf("%d\n",Calc(1-2));
```

大多数人以为这个程序输出结果是$2$，他们是这么计算的：

$x=1-2=-1$，$Calc(x)=Calc(-1)=1-(-1)=2$

但是，别忘记$define$是纯文本替换，所以其实是这个样子的：

$Calc(x)=Calc(1-2)=1-1-2=4$

惊不惊喜，意不意外？

所以建议这么写

```cpp
#define Calc(x) 1-(x)
```

3.树剖的查询和线段树的查询写反