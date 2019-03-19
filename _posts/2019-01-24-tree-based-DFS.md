---
title: Tree-based DFS
description: Summary of DFS.
categories:
 - Leetcode
tags:
 - DFS
---
# Tree-based DFS
Basically, there are four ways to traverse a Tree:
1. Level order
2. Pre order
3. In order
4. Post order

We can use BFS to get the level order traversal. However, we need DFS to get the other three orders of traversal.
## Traversal
![fig. 1](http://media.jiuzhang.com/markdown/images/3/15/d77b07ce-27f7-11e8-9f14-0242ac110002.jpg)
1. Level order (BFS)
2. Pre order (root->left tree->right tree)

ABDECF
```python
def pre_order(root, result): # recursion
    if root is None:
         return
    result.append(root.val)
    traverse(root.left, result)
    traverse(root.right, result)
```
```python
def preorder_non_recursion(root):
    stack = []
    preorder = []
    if not root:
        return preorder
    stack.append(root)
    while len(stack) > 0:
        node = stack.pop()
        preorder.append(node.val)
        if node.right:
            stack.append(node.right)
        if node.left:
            stack.append(node.left)
    return preorder
```
3. In order (left tree->root->right tree)

DBEAFC

⭐️中序遍历是一个升序序列
```python
def in_order(root, result): # recursion
    if root is None:
        return
    traverse(root.left, result)
    result.append(root.val)
    traverse(root.right, result)
```
4. Post order

DEBFCA
```python
def post_order(root, result): # recursion
    if root is None:
        return
    traverse(root.left, result)
    traverse(root.right, result)
    result.append(root.val)
```
# Binary Tree三大考点
## 求值，求路径
## 结构变化
## BST