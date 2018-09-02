---
layout: post
title: python中的最大字串
taggs: python
tag: [python]
issueID: 7
---

##矩阵法找最大子串
```
def findit(str1:str, str2:str):
    if len(str2) < len(str1):
        str1,str2 = str2,str1
    length1 = len(str1)  ##最短的字符串
    length2 = len(str2)
    matrix = [[0] * length1 for i in range(length2)]
    print(matrix)
    xmax = 0
    xindex = 0
    
    for i,x in enumerate(str2):
        for j,y in enumerate(str1):
            if x != y:  ### 0
                pass
            else:
                if i == 0 or j == 0:
                    matrix[i][j] = 1  ###在边上
                else:
                    #pre = matrix[i-1][j-1]
                    #if pre > 0:
                    #    matrix[i][j] = pre + 1
                    matrix[i][j] = matrix[i-1][j-1] + 1
                    
                    if matrix[i][j] > xmax:
                        xmax = matrix[i][j]   ###记录最大值
                        xindex = j

    print(matrix, xmax, xindex)
    
    start = xindex + 1 -xmax
    end = xindex + 1
    
    #print(str1[start:end])
    return str1[start:end] 


s1 = 'dabce'
s2 = 'abcdefg'

print(findit(s1,s2))
```

##常规方法求最大子串
```
def long_substr(b='abcd',a='dbc'):
    
    len_a = len(a)
    len_b = len(b)
    #if len_a < len_b:
    #    a,b = b,a
    maxi = 0
    max_str =''
    str2 = ''
    len_str2 = 0
    start_str2 = 1
    
    for i in range(len_a):
        for j in range(len_b):
            if not len_str2 and a[i] == b[j]:
                len_str2 += 1
                str2 += b[j]
                start_str2 = j
            if len_str2 and i+len_str2 < len_a:
                #print(i+len_str2) 
                if a[i+len_str2] == b[j]:
                    str2 += b[j]
                    len_str2 += 1
            #else:
            #    len_str2 = 0
            #    break
        #print(maxi)        
        if maxi < len_str2:
            maxi = len_str2
            max_str = str2
            #print(max_str)
            str2 = ''
            len_str2 = 0
    return max_str


long_substr()
```
