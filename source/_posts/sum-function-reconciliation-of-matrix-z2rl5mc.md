---
title: sum函数对矩阵的求和
date: '2024-12-28 21:44:16'
updated: '2025-01-25 23:25:59'
tags:
  - MatLab
permalink: /post/sum-function-reconciliation-of-matrix-z2rl5mc.html
comments: true
toc: true
---



‍

```matlab
    A= [1， 2 ，3 ，4， 5；
		1， 2， 3， 4， 5]；
```

```matlab
 a=sum(A)   %对整个矩阵按列求和

 >> a= [2 4 6 8 10]
```

```matlab
 sum(A(1:t,:),1)    %对矩阵前1到t行按列求和
```

```matlab
 b=sum(A,2) %对整个矩阵按行求和

 >>b=[15;15];
```

```matlab
 d=sum(A(:,1:3),2)  %对矩阵前1到3列按行求和

 >>d = [6;6]
```

```matlab
 c=sum(A(:)) %整个矩阵整体求和

 >>c =30
```

 A(:,1)是求矩阵的第一列

 A(1,:)是求矩阵的第一 行
