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
DP– optimal structure– best total of all houses depends on the best totals of smaller groups of houses
overlapping subproblems– the same smaller problems appear several times

stores the results of these smaller problems and reuses them

bottom-up dynamic programming: we start from the smallest cases (first house, first two) and build up using the max_money array

**Time & Space Complexity:**
Time Complexity: 0(n) – only goes through the list once; constant number per house

Space Complexity: 0(n) – for the max_money, I used a list size of n to store the results for each house

**Code w/ Comments:**
def rob(nums):
    n = len(nums) –we find the number of houses
    if n == 0: –no house, no rob
        return 0
    if n == 1: –1 house, rob 
        return nums[0]
  
   max_money = [0] * n  –list of length n
   max_money[0] = nums[0] –base case: first house available, best is to rob
   max_money[1] = max(nums[0], nums[1]) –best case for 2 houses: only rob one, not two, so we take the larger amount

   for i in range(2, n): –we determine from each house from 2 to n-1 the bests possible total up to that house
   max_money[i] = max(max_money[i-1], max_money[i-2] + nums[i]) –recurrence; we either skip house i, and stay max, or rob house i, we can't rob i-1, so we add nums[i] to the  best total from 1-2.. it takes whichever gives a larger total

  return max_money[-1]
