---
title: "删除链表的倒数第 N 个结点"
date: 2023-07-04T00:40:30+08:00
draft: false
categories: ["算法",]
tags: ["链表", "双指针", "快慢指针"]
---

## Leetcode 19. 删除链表的倒数第 N 个结点
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

<!--more-->

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy_head = ListNode(next=head)
        slow = dummy_head
        fast = head

        while fast:
            if n:
                n -= 1
            else:
                slow = slow.next
            fast = fast.next
        
        slow.next = slow.next.next

        return dummy_head.next

```
