---
title: "前 K 个高频元素"
date: 2023-07-11T20:30:05+08:00
draft: true
---

## Leetcode 347. 前 K 个高频元素
给你一个整数数组 nums 和一个整数 k ，请你返回其中出现频率前 k 高的元素。你可以按 任意顺序 返回答案。

<!--more-->

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        f_map = {}
        pri_que = []
        res = [0] * k

        for i in range(len(nums)):
            f_map[nums[i]] = f_map.get(nums[i], 0) + 1

        for key, freq in f_map.items():
            heapq.heappush(pri_que, (freq, key))
            if len(pri_que) > k:
                heapq.heappop(pri_que)

        for i in range(k - 1, -1, -1):
            res[i] = heapq.heappop(pri_que)[1]

        return res

```
