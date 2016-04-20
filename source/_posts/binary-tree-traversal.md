---
title: 二叉树遍历的非递归算法
date: 2016-04-19 13:05:52
category: 学习笔记
tags: Algorithms
---

为了把一个递归过程改为非递归过程，一般需要利用一个工作栈，记录遍历时回退路径

二叉树结点类的定义
```python
class TreeNode(object):
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
```
<!--more-->

## 前序遍历
为了保证先左子树后右子树的顺序，在进栈时先进右子结点的地址，后进左子结点的地址
```python
def preOrder(root):
    # root的类型为 TreeNode
    if not root:
        return
    s = [root]
    while s:
        p = s.pop()
        print p.val
        if p.right: s.append(p.right) 
        if p.left: s.append(p.left) 
```

## 中序遍历
```python
def inOrder(root):
    if not root:
        return 

```
