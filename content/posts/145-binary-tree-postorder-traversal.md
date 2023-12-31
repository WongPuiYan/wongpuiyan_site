---
title: "二叉树的后序遍历"
date: 2023-07-11T23:42:43+08:00
draft: false
categories: ["算法",]
tags: ["树", "二叉树", "递归"]
---

## Leetcode 145. 二叉树的后序遍历
给你一棵二叉树的根节点 root ，返回其节点值的 后序遍历 。

<!--more-->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# 递归
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root is None:
            return []

        left = self.postorderTraversal(root.left)
        right = self.postorderTraversal(root.right)

        return [*left, *right, root.val]

# 迭代
class Solution:
   def postorderTraversal(self, root: TreeNode) -> List[int]:
       if not root:
           return []
       stack = [root]
       result = []

       while stack:
           node = stack.pop()
           # 中结点先处理
           result.append(node.val)
           # 左孩子先入栈
           if node.left:
               stack.append(node.left)
           # 右孩子后入栈
           if node.right:
               stack.append(node.right)

       # 将最终的数组翻转
       return result[::-1]

class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        result = []
        st = []

        if root:
            st.append(root)

        while st:
            node = st.pop()
            if node != None:
                st.append(node) #中
                st.append(None)

                if node.right: #右
                    st.append(node.right)
                if node.left: #左
                    st.append(node.left)
            else:
                node = st.pop()
                result.append(node.val)

        return result

```
