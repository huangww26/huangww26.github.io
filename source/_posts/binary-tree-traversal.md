---
title: 二叉树遍历的非递归算法
date: 2016-04-19 13:05:52
category: 学习笔记
tags: Algorithms
---

为了把一个递归过程改为非递归过程，一般需要利用一个工作栈，记录遍历时回退路径

## 前序遍历
```python
class TreeNode(object):
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def preOrder(root):
    # :type root: TreeNode
    if not root:
        return
    stack = [root]
    while stack:
        p = stack.pop()
        print p.val
        if p.right: stack.append(p.right) 
        if p.left: stack.append(p.left) 
```
