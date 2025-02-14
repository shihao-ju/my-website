---
title: 'DSA - Day 2'
date: 2025-02-12
tags: [Programming]
draft: false
hideInList: false
feature: 
isTop: false
---

# KarmaCoder Day 2 LC209/59

1️⃣ Minimum size subarray sum
Link: [lc209](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

Key points:
1. Two pointers: one goes through the array, the other updates the subarray start to make sure the length is minimum.
2. Once the first pointer moves to a position where the sum reaches target, the second pointer starts to narrow the length of subarray as much as possible while maintaing the sum equal to or larger than the target. 

Time complexity: O(n)
Space complexity: O(1)

```python
def minSubArrayLen(self, target: int, nums: List[int]) -> int:
  start, sum = 0, 0, 0
  min_len = float('Inf')
  for i in range(len(nums)):
      sum += nums[i]
      while sum >= target:
          min_len = min(min_len, i - start + 1)
          sum -= nums[start]
          start += 1
  return min_len if min_len != float('Inf') else 0
```

2️⃣ Spiral matrix
Link: [lc59](https://leetcode.com/problems/spiral-matrix-ii/description/)

Key points:
1. Python can directly initialize a 2D array, but note that `[[0] * n for _ in range(n)]` is different from `[[0] * n] * n`. Don't use the second way in most cases because it creates multiple references to the same inner list, which means updating one inner list appears in all rows because they are the same object.
2. The outer for loop controls how many loops we need to circle, ignoring the center element if n is odd (which will be filled at the end)
3. Inside the outer loop, four parallel inner for loops correspond to four sides note that each inner loop follows the same range pattern (ex. left-inclusive, right-exclusive) 

Time complexity: O(n)
Space complexity: O(1)

```python
def generateMatrix(self, n: int) -> List[List[int]]:
  x = 0
  y = 0
  loop, mid = n//2, n//2
  result = [[0] * n for _ in range(n)]
  idx = 1
  for offset in range(1, loop + 1):
      for i in range(y, n - offset):
          result[x][i] = idx
          idx += 1
      for i in range(x, n - offset):
          result[i][n - offset] = idx
          idx += 1
      for i in range(n - offset, y, -1):
          result[n - offset][i] = idx
          idx += 1
      for i in range(n - offset, x, -1):
          result[i][y] = idx
          idx += 1
      x += 1
      y += 1

  if n % 2 != 0:
      result[mid][mid] = idx
  return result
```

An alternative method given on the karma is more clear, which defines the four sides as top, bottom, left, and right. Every time a side is filled up, that side is added 1 as an update. The outer while loop control make sures top >= bottom and left <= right. It also handles the center element naturally.
```python
if n <= 0:
   return []

# Initialize square matrix
matrix = [[0]*n for _ in range(n)]

# Initialize sides
top, bottom, left, right = 0, n-1, 0, n-1
num = 1

while top <= bottom and left <= right:
   # fill top
   for i in range(left, right + 1):
       matrix[top][i] = num
       num += 1
   top += 1

   # fill right
   for i in range(top, bottom + 1):
       matrix[i][right] = num
       num += 1
   right -= 1

   # fill bottom
   for i in range(right, left - 1, -1):
       matrix[bottom][i] = num
       num += 1
   bottom -= 1

   # fill left
   for i in range(bottom, top - 1, -1):
       matrix[i][left] = num
       num += 1
   left += 1

return matrix
```

3️⃣ Sum of interval 1D and 2D

Key points:
1. the sum of an interval in an array can be calculated by the difference between the prefix sum of the two end positions.