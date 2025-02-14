---
title: 'DSA - Day 1 Array I'
date: 2025-02-11
tags: [Programming]
draft: false
hideInList: false
feature: 
isTop: false
---

# KarmaCoder Day 1 LC704/27/977

1️⃣ Binary search
Link: [lc704](https://leetcode.com/problems/binary-search/description/)

Key points:
1. The principle is the range definition, either a double-closed range [A, B] or a left-closed right-open range [A, B)
2. the while loop condition depends on the range definition:
	1. double-closed: `left <= right` is valid
	2. left-closed right open: `left < right` is valid.
3. the if-else statement depends on the range definition:
	1. double-closed: the updated left or right does not include mid
	2. left-closed right open: the updated right can include mid
4. Similarly, right is initialized to numsSize - 1 or numsSize also depends on the range definition. 

Time complexity: O(logn)
Space complexity: O(1)

```python
def search(self, nums: List[int], target: int) -> int:
  left = 0
  right = len(nums)
  while left < right:
      mid = (left + right) // 2
      if target < nums[mid]:
          right = mid
      elif target > nums[mid]:
          left = mid + 1
      else:
          return mid
  return -1
```

2️⃣ Remove element
Link: [lc27](https://leetcode.com/problems/remove-element/description/)
Key points:
1. Use two pointers, fast and slow.
2. Fast pointer points to the to-be-recorded element in the original array
3. Slow pointer points to the new location for the to-be-recorded element.

Time complexity: O(n)
Space complexity: O(1)

```python
def removeElement(self, nums: List[int], val: int) -> int:
  slow = 0
  for i in range(len(nums)):
      if nums[i] != val:
          nums[slow] = nums[i]
          slow += 1
  return slow
```

3️⃣ Squares of a sorted array
Link: [lc977](https://leetcode.com/problems/squares-of-a-sorted-array/description/)
Key points:
1. Use two pointers, head and tail.
2. A third pointer writes the larger data between head and tail pointers into the result array
```python
def sortedSquares(self, nums: List[int]) -> List[int]:
  i = 0
  j = len(nums) - 1
  k = j
  sorted_nums = [0.0] * len(nums)
  while i <= j:
      if nums[i] * nums[i] > nums[j] * nums[j]:
          sorted_nums[k] = nums[i] * nums[i]
          i += 1
      else:
          sorted_nums[k] = nums[j] * nums[j]
          j -= 1
      k -= 1
  return sorted_nums
```