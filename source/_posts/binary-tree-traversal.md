---
title: 二叉树遍历的非递归算法
date: 2016-04-19 13:05:52
category: 学习笔记
tags: Algorithm
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
    p = root    # 用p指向下一个待访问的结点
    s = []
    while p or s:
        if p:               # 如果p非空，把p入栈，然后p指向坐子结点
            s.append(p)
            p = p.left
        else:               # 如果p空，则弹出栈顶元素进行访问，然后p指向右子结点
            p = s.pop()
            print p.val     # 访问p
            p = p.right
```

## 后序遍历
第一种思路：另外定义一个入栈的类型，加多一个变量记录结点是否第一次入栈，如果是则表明该结点的右子树还没访问(如果有的话)，则暂时还不能访问该结点
```python
class BTNode(object):
    def __init__(self):
        self.treeNode = None
        self.isFirst = True

def postOrder(root):
    if not root:
        return 
    p = root
    s = []
    while p or s:
        while p:
            btn = BTNode()
            btn.treeNode = p
            bt.isFirst = True
            s.append(bt)
            p = p.right
        if s:
            temp = s.pop()
            if temp.isFirst:
                temp.isFirst = False
                s.append(temp)
                p = temp.treeNode.right
            else:
                print temp.treeNode.val
```

第二种思路：对于任意结点p，先将其入栈。如果p不存在左右子结点，则直接访问它；如果p的左右子界结点都访问过了，则也可以直接访问它；否则将p的右子节点和左子结点依次进栈
```python
def postOrder(root):
    if not root:
        return
    s = []
    cur = pre = None
    s.append(root)
    while s:
        cur = s[-1]     # 此处不能先pop出栈顶元素
        if (cur.left == None and cur.right == None) or (pre and (pre == cur.left or pre == cur.right)):
            print cur.val
            s.pop()
            pre = cur
        else:
            if cur.right: s.append(cur.right)
            if cur.left: s.append(cur.left)
```
