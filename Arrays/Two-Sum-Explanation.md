# Two Sum

## Problem

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to the target.

---

## Approach

We use a HashMap (Dictionary).

For every number:

1. Calculate the complement

   complement = target - num

2. Check if the complement already exists in the HashMap.

3. If yes, return both indices.

4. Otherwise store the current number and its index.

---

## Example

nums = [2,7,11,15]

target = 9

Step 1:

Current number = 2

Complement = 9 - 2 = 7

Store:

{2:0}

Step 2:

Current number = 7

Complement = 9 - 7 = 2

2 already exists in the HashMap.

Answer = [0,1]

---

## Python Solution

```python
class Solution:
    def twoSum(self, nums, target):

        hashmap = {}

        for i, num in enumerate(nums):

            complement = target - num

            if complement in hashmap:
                return [hashmap[complement], i]

            hashmap[num] = i
