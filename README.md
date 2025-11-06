# Algorithm_Quiz_Option2

**Problem Description:**
Option 2: House Robber (LeetCode #198) - Medium
Asked at: Google, Amazon, Meta, Apple
Problem Statement: You are a professional robber planning to rob houses along a street.
Each house has a certain amount of money stashed. The only constraint stopping you from robbing
each of them is that adjacent houses have security systems connected, and it will automatically
contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the max-
imum amount of money you can rob tonight without alerting the police.

Example:
• Input: nums = [2, 7, 9, 3, 1]
• Output: 12
• Explanation: Rob house 1 (money = 2), rob house 3 (money = 9), and rob house 5 (money
= 1). Total = 2 + 9 + 1 = 12

**Approach Explanation:**


**Time & Space Complexity:**
Time Complexity: 



**Code w/ Comments:**
def rob(nums):
  n = len(nums)
  if n == 0:
    return 0
  if n == 1:
    return nums[0]

 max_money = [0] * n
 max_money[0] = nums[0]
 max_money[1] = max(nums[0], nums[1])

 for i in range(2, n):
   max_money[i] = max(max_money[i-1], max_money[i-2] + nums[i])

return max_money[-1]
