---
layout: post
title: python计算质数的方法和改进
taggs: math, python
tag: [math, python]
issueID: 3
---

# 充分利用前面已经查找出来的质数结果, 继续进行查找质数
```
import datetime

ss = [2]
count = 1
n = 100  ###100内质数有25个

start = datetime.datetime.now()

for i in range(3,n,2):
    edge = i ** 0.5  ###不能每一次算一次 开平方根
    for k in ss:
        ### 改进点 复用,利用以前(上次)的计算结果,大大提高效率
        if i % k == 0:  ###找到了合数
            break
        ###if k > i ** 0.5:  ###找到了质数k, 不能每次算一次开平方根
        if k > edge:    
            count += 1
            ss.append(i)
            break

delta =(datetime.datetime.now() - start).total_seconds()
print(delta)

print(count)        
for j in s:
    print(j,end=' ')
```

# 质数性质(n>3的质数都出现在6n-1,或6n-1)
```
count = 2
n = 100
x = 5  ###质数出现在6n-1, 6n+1上
step =2
s = [2,3,5]

while x <= n:
    edge = x ** 0.5
    for k in s:
        ### 改进点 复用,利用以前(上次)的计算结果,大大提高效率
        if x % k == 0:  ###找到了合数
            break
        ###if k > i ** 0.5:  ###找到了质数k, 不能每次算一次开平方根
        if k > edge:    
            count += 1
            s.append(x)
            break
        
    x += step
    step = 4 if step == 2 else 2  ###变步长
        
print(count)
```

# 筛法
```
import numpy as np
num_prime = 0
isprime = np.zeros(101)
prime = np.zeros(101)

for i in range(2,100):
    #print(i,'  ---------------------------')
    if isprime[i] == 0:
        prime[num_prime] = i
        #print(i)
        #print(num_prime,'---')
        num_prime += 1
    for j in range(num_prime):
        if i * prime[j] > 100:
            break
        #print('===',j,'===')
        isprime[int(i * prime[j])] = 1
        #print(int(i * prime[j]),'***')
        #print(int(prime[j]),'xxxx')
        if i % prime[j] == 0:
            break
            # 关键在于这个 if 语句，在检测到其i 可以被整除时退
            # 出循环，即每次只寻找到素数最小的质因数,不会被重
            # 复标记

print([i for i in range(2,100) if isprime[i] == 0])
```
