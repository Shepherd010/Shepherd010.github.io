---
title: 添加图标题、轴标签、图例、更改字体大小
date: '2024-12-28 21:45:29'
updated: '2025-01-25 23:21:21'
excerpt: >-
  本文介绍了在MATLAB中向图形添加标题、轴标签和图例的基本方法。首先，通过`title`函数可以为绘制的图形添加标题；使用`xlabel`和`ylabel`函数分别设置x轴和y轴的标签。此外，`legend`函数用于根据绘图顺序添加图例，以便更清晰地标识不同的数据线。最后，使用`'FontSize'`属性可以调整标题、标签及图例的字体大小，以提高可读性。文章通过多个示例展示了这些功能的具体用法与效果，并提供了相关链接以获取更多信息。
tags:
  - MatLab
permalink: /post/add-icon-title-axis-label-legend-change-the-font-size-z1k0xte.html
comments: true
toc: true
---

# 添加图标题、轴标签、图例、更改字体大小

### 1 添加标题

 `title`​：向图中添加标题

 示例：

```cpp
clc;
clear;

% 绘制
x = linspace(0,2*pi);
y = sin(x) - tan(sin(x));
plot(x,y)
title('y = sin(x)-tan(sin(x))')
```

 **结果展示：**

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205449015.png)​

### 2 添加轴标签

 `xlabel`​：x轴标签  
 `ylabel`​：y轴标签  
 `zlabel`​：z轴标签（plot3）

 **示例：**

```cpp
clc;
clear;

% 绘制
x = linspace(0,2*pi);
y = sin(x)-tan(sin(x));
plot(x,y)
title('y = sin(x) - tan(sin(x))')
xlabel('X(m)')
ylabel('Y(m)')
```

 **结果展示：**

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205449516.png)​

### 3 添加图例

 `legend`​：按绘图顺序添加图例

 示例：

```cpp
clc;
clear;

% 绘制
x = linspace(0,2*pi);
y = sin(x)-tan(cos(x));

plot(x,sin(x))
hold on
plot(x,cos(x))
hold on
plot(x,tan(cos(x)))
hold on
plot(x,y)
hold off

title('添加图例')
xlabel('X(m)')
ylabel('Y(m)')
% 按绘图顺序添加图例
legend('y = sin(x)','y = cos(x)','y = tan((cos(x))','y = sin(x) - tan(cos(x))')
```

 **结果展示：**

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205450057.png)​

### 4 更改标题、标签、图例的字体大小

 `'FontSize'`​ 字号属性

 **示例：**

```cpp
clc;
clear;

% 绘制
x = linspace(0,2*pi);
y = sin(x)-tan(cos(x));

plot(x,sin(x))
hold on
plot(x,cos(x))
hold on
plot(x,tan(cos(x)))
hold on
plot(x,y)
hold off

title('添加图例','FontSize',20)
xlabel('X/(m)','FontSize',15)
ylabel('Y/(m)','FontSize',10)
% 按绘图顺序添加图例
legend('y = sin(x)','y = cos(x)','y = tan((cos(x))','y = sin(x) - tan(cos(x))')
```

 **结果展示：**

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205450592.png)​

---

 **相关链接**

 [https://ww2.mathworks.cn/help/matlab/creating\_plots/add-title-axis-labels-and-legend-to-graph.html](https://ww2.mathworks.cn/help/matlab/creating_plots/add-title-axis-labels-and-legend-to-graph.html)

‍
