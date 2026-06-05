# 242. Valid Anagram

## Problem Statement

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

### Example 1

Input:
```text
s = "anagram"
t = "nagaram"
```

Output:
```text
true
```

### Example 2

Input:
```text
s = "rat"
t = "car"
```

Output:
```text
false
```

---

# Approach: HashMap (Dictionary)

An anagram contains:

- Same characters
- Same frequency of characters
- Order does not matter

We use two dictionaries to count how many times each character appears in both strings.

If both dictionaries become equal, the strings are anagrams.

---

# Python Solution

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:

        if len(s) != len(t):
            return False

        countS = {}
        countT = {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)

        return countS == countT
```

---

# Code Explanation

## Step 1: Check Length

```python
if len(s) != len(t):
    return False
```

If the lengths are different, they can never be anagrams.

Example:

```text
"cat" = 3 characters
"cats" = 4 characters
```

Output:

```text
False
```

---

## Step 2: Create Dictionaries

```python
countS = {}
countT = {}
```

These dictionaries store character frequencies.

Example:

```python
{
'a': 3,
'n': 1
}
```

Meaning:

```text
'a' appears 3 times
'n' appears 1 time
```

---

## Step 3: Traverse Both Strings

```python
for i in range(len(s)):
```

Visit each character one by one.

Example:

```text
i = 0
i = 1
i = 2
...
```

---

## Step 4: Count Characters

```python
countS[s[i]] = 1 + countS.get(s[i], 0)
```

### Understanding .get()

```python
countS.get('a', 0)
```

Means:

- Return the value of 'a' if it exists
- Otherwise return 0

Example:

```python
{}
```

```python
countS.get('a',0)
```

Output:

```text
0
```

Then:

```python
countS['a'] = 1 + 0
```

Result:

```python
{'a':1}
```

---

## Step 5: Do the Same for t

```python
countT[t[i]] = 1 + countT.get(t[i], 0)
```

This counts character frequencies in the second string.

---

## Step 6: Compare Both Dictionaries

```python
return countS == countT
```

If frequencies match exactly:

```python
countS = {'a':3,'n':1,'g':1,'r':1,'m':1}
countT = {'a':3,'n':1,'g':1,'r':1,'m':1}
```

Output:

```text
True
```

Otherwise:

```text
False
```

---

# Dry Run

Input:

```text
s = "anagram"
t = "nagaram"
```

After counting:

```python
countS = {
'a':3,
'n':1,
'g':1,
'r':1,
'm':1
}
```

```python
countT = {
'n':1,
'a':3,
'g':1,
'r':1,
'm':1
}
```

Comparison:

```python
countS == countT
```

Output:

```text
True
```

---

# Time Complexity

```text
O(n)
```

We traverse the strings only once.

---

# Space Complexity

```text
O(1)
```

Only lowercase English letters are used, so the number of unique characters is limited.

---

# Key Learning

- HashMap (Dictionary) stores character frequencies.
- Frequency counting is a common interview pattern.
- Two strings are anagrams if all character frequencies match.
- This approach is efficient with O(n) time complexity.
