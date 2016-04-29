---
title: 全排列算法
date: 2016-04-08 20:08:56
category: 学习笔记
tags: Algorithm
---

用递归算法给出生成A=[1,2,...,n]的全排列
``` python
def Perm(A, strt, end):
    """产生A[strt:end]的所有全排列"""
    if strt == end:
        print ''.join([str(i) for i in A])
    else:
        for i in range(strt, end+1):  
            A.insert(strt, A.pop(i))        # 保证按字典顺序输出
            Perm(A, strt+1, end)
            A.insert(strt, A.pop(i))
```
