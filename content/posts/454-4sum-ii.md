---
title: "四数相加 II"
date: 2023-07-05T22:36:18+08:00
draft: false
categories: ["算法",]
tags: ["哈希表", "双指针", "快慢指针"]
---

## Leetcode 454. 四数相加 II
给你四个整数数组 nums1、nums2、nums3 和 nums4 ，数组长度都是 n ，请你计算有多少个元组 (i, j, k, l) 能满足：

* 0 <= i, j, k, l < n
* nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0

<!--more-->

```python
class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:
        records = dict()
        count = 0

        for n1 in nums1:
            for n2 in nums2:
                records[n1 + n2] = records.get(n1 + n2, 0) + 1
        
        for n3 in nums3:
            for n4 in nums4:
                key = - n3 - n4
                if key in records:
                    count += records[key]
        
        return count

```
 