---
layout: post
title: python用数学关系和坐标打印点图
taggs: math, python
tag: [math, python]
issueID: 3
---

## 用数学方程式关系和坐标系观点,用两个for循环模拟xy轴,来控制点在图的位置,同时还能可以比较方便的变换图形
```
           |
           |
           |
---------------------->   x轴
           |
           |
           |
           V
           y轴
```

## 打印矩形
```
### c方法, 坐标, 直线, 其它位置输出' 
n=10
for i in range(1, n+1):
    for j in range(1, n+1):
        if i==1 or j==1 or i==n or j==n:
            print('*',end=' ')
        else:
            print(' ',end=' ')
    print() ###打印空行


* * * * * * * * * * 
*                 * 
*                 * 
*                 * 
*                 * 
*                 * 
*                 * 
*                 * 
*                 * 
* * * * * * * * * * 
```

## 打印菱形
```
e = 7//2
for i in range(-e,e+1):
    print(' '* abs(i),end='')
    for j in range(-e,e+1):
        ###坐标中心点,可打点的范围
        if abs(i) + abs(j) <4:
            print('*',end='')
    print()


   *
  ***
 *****
*******
 *****
  ***
   *
```

## 镂空菱形
```
e = 10//2
for i in range(-e,e+1):
    #print(' '* abs(i),end='')
    for j in range(-e,e+1):
        ###坐标中心点,可打点的范围
        if abs(i) + abs(j) >e:
            #print(j)
            #if j == 0:
            #    print('-', end='')
            print('*',end='')
        else:
            print(' ',end='')
    print()


***** *****
****   ****
***     ***
**       **
*         *
           
*         *
**       **
***     ***
****   ****
***** *****
```

## 打印闪电
```
e = 7//2
for i in range(-e,e+1):
    for j in range(-e,e+1):
        if abs(i) + abs(j) <=3:
            if i <=0 and j <=0:
                print('*',end='')
            elif i >=0 and j >=0:
                print('*',end='')
            else:
                print(' ',end='')
        
        else:
            print(' ',end='')
    print()


   *   
  **   
 ***   
*******
   *** 
   **  
   *   
```



