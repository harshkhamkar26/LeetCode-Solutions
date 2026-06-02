# Contains Duplicate (LeetCode 217)

## Problem Statement

Given an integer array `nums`, return:

* `True` if any value appears at least twice in the array.
* `False` if every element is distinct.

### Example 1

```python
Input: nums = [1,2,3,1]

Output: True
```

Explanation:

The number `1` appears more than once.

---

### Example 2

```python
Input: nums = [1,2,3,4]

Output: False
```

Explanation:

All elements are unique.

---

## Optimal Approach: Using HashSet

### What is a HashSet?

A HashSet is a data structure that stores only unique values.

In Python, a `set` acts as a HashSet.

Example:

```python
nums = [1,2,3,1]

set(nums)
```

Output:

```python
{1,2,3}
```

Notice that the duplicate value `1` is automatically removed.

---

## Logic

We create an empty HashSet.

While traversing the array:

1. Check if the current number already exists in the HashSet.
2. If it exists, a duplicate is found, so return `True`.
3. Otherwise, add the number to the HashSet.
4. If the loop finishes, return `False`.

---

## Code

```python
class Solution:
    def containsDuplicate(self, nums):
        hashset = set()

        for num in nums:

            if num in hashset:
                return True

            hashset.add(num)

        return False
```

---

## Line-by-Line Explanation

### Create an Empty HashSet

```python
hashset = set()
```

Creates an empty set to store unique numbers.

Example:

```python
{}
```

---

### Traverse the Array

```python
for num in nums:
```

Visits every number one by one.

Example:

```python
nums = [1,2,3,1]
```

Iteration Order:

```python
1 → 2 → 3 → 1
```

---

### Check for Duplicate

```python
if num in hashset:
```

Checks whether the current number already exists in the HashSet.

If yes, we have found a duplicate.

---

### Return True

```python
return True
```

Immediately returns `True` because a duplicate has been found.

---

### Add Current Number

```python
hashset.add(num)
```

Adds the current number to the HashSet.

Example:

```python
hashset = {1}
```

then

```python
hashset = {1,2}
```

then

```python
hashset = {1,2,3}
```

---

### No Duplicate Found

```python
return False
```

If the loop completes without finding duplicates, all elements are unique.

---

## Dry Run

### Input

```python
nums = [1,2,3,1]
```

### Step 1

```python
hashset = {}
```

Current number:

```python
1
```

Add to HashSet:

```python
{1}
```

---

### Step 2

Current number:

```python
2
```

Add to HashSet:

```python
{1,2}
```

---

### Step 3

Current number:

```python
3
```

Add to HashSet:

```python
{1,2,3}
```

---

### Step 4

Current number:

```python
1
```

Check:

```python
1 in {1,2,3}
```

Result:

```python
True
```

Duplicate found.

Return:

```python
True
```

---

## Complexity Analysis

### Time Complexity

```text
O(n)
```

We traverse the array only once.

---

### Space Complexity

```text
O(n)
```

In the worst case, all elements are unique and stored in the HashSet.

---

## Key Learning

* HashSet stores only unique values.
* HashSet provides very fast lookup operations.
* Before adding a value, we check if it already exists.
* If it exists, we immediately know a duplicate is present.
* This reduces the complexity from **O(n²)** (Brute Force) to **O(n)**.

### Interview Tip

Whenever a problem involves:

* Finding duplicates
* Checking uniqueness
* Fast lookups

Think about using a **HashSet**.



Approach 2: Brute Force
Logic

Compare every element with every other element.

If any two elements are equal, return True.

Otherwise return False.

Code
class Solution:
    def containsDuplicate(self, nums):
        n = len(nums)

        for i in range(n):
            for j in range(i + 1, n):

                if nums[i] == nums[j]:
                    return True

        return False
Time Complexity
O(n²)

Because every element is compared with every other element.

Space Complexity
O(1)

No extra space is used.
