---
title: "反转链表"
date: 2023-07-04T00:18:49+08:00
draft: false
categories: ["算法",]
tags: ["链表", "双指针"]
---

## Leetcode 206. 反转链表
给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。

<!--more-->

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        cur = head
        pre = None

        while cur:
            tmp = cur.next
            cur.next, pre = pre, cur
            cur = tmp
        
        return pre

```
