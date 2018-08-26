---
layout: post
title: python递归中的传参
taggs: python
tag: [python]
issueID: 6
---

## 递归中传参,提高递归的效率, 特别是充分利用前面已经计算出来的部分结果

## 猴子和桃子数量
猴子第一天摘下若干个桃子，当即吃了一半，还不过瘾，又多吃了一个。第二天早上又将剩下的桃子
吃掉一半，又多吃了一个。以后每天早上都吃了前一天剩下的一半零一个。到第10天早上想吃时，只
剩下一个桃子了。求第一天共摘多少个桃子。
```
def peach(days=10,a=1):
    if days == 1:
        return a
    a = (a + 1) * 2
    return peach(days-1,a)   ###传递的参数a是经过叠加计算的值

peach(10)
```

## 遍历树,得到叶子的路径
源字典:  d = {'a':{'b':1, 'c':2},'d':{'e':3, 'f':{'g':4}}}
  a           d
b   c       e   f
1   2       3   g
                4

a.b    a.c    d.e    d.f.g
 1      2      3       4
            

```
d = {'a':{'b':1, 'c':2},'d':{'e':3, 'f':{'g':4}}}
#d = {'a':{'h':{'i':{'b':1}}, 'c':2},'d':{'e':3, 'f':{'g':4}}}

def plat(t, tmp=''):
    if isinstance(t, dict):
        for i in t:
            plat(t[i],tmp+i)  ###传递了各条路径上的依次节点序列
        ###if isinstance(t[i], dict):
        ###    tmp += i
    else:
        #return tmp
        print('.'.join(tmp),'===>',t)
        ###tmp = ''
        
plat(d)

#a----   b--plat('b')  ---c--plat('c')
#d---    e--
```
