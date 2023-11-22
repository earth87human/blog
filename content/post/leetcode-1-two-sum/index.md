---
title: Leetcode 1 Two Sum
date: 2023-04-01
slug: leetcode-1-two-sum
tags: 
    - easy
    - array
categories:
    - Leetcode
---

## Problem :

### Description

> Given an array of integers <kbd>nums</kbd> and an integer <kbd>target</kbd> , return indices of the two numbers such that they add up to <kbd>target</kbd>.  

> You may assume that each input would have ***exactly one solution*** , and you may not use the same element twice.  

> You can return the answer in any order.  

### Example 1

> **Input** : nums = [2,7,11,15] , target = 9  
> **Output** : [0,1]  
> **Explanation** : Because nums[0] + nums[1] == 9, we return [0, 1].  

### Example 2

> **Input** : nums = [3,2,4] , target = 6  
> **Output** : [1,2]  

### Example 3

> **Input** : nums = [3,3] , target = 6  
> **Output** : [0,1]  

### Constraints

* <kbd>2 <= nums.length <= 10<sup>4</sup></kbd>
* <kbd>-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup></kbd>
* <kbd>-10<sup>9</sup> <= target <= 10<sup>9</sup></kbd>
* **Only one valid answer exists.**

## Solution 1 : Brute Force

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {}; // No solution found
    }
};

# 時間複雜度 Ｏ(n^2)
# 空間複雜度 Ｏ(1)
```

## Solution 2 : Two-pass Hash Table

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> numMap;
        int n = nums.size();

        // Build the hash table
        for (int i = 0; i < n; i++) {
            numMap[nums[i]] = i;
        }

        // Find the complement
        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.count(complement) && numMap[complement] != i) {
                return {i, numMap[complement]};
            }
        }

        return {}; // No solution found
    }
};

# 時間複雜度 Ｏ(n)
# 空間複雜度 Ｏ(n)
```

## Solution 3 : One-pass Hash Table

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> numMap;
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.count(complement)) {
                return {numMap[complement], i};
            }
            numMap[nums[i]] = i;
        }

        return {}; // No solution found
    }
};

# 時間複雜度 Ｏ(n)
# 空間複雜度 Ｏ(n)
```

## 大功告成～