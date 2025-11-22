# code-umbrella:


```def contains_duplicate(nums):
    seen = set()                       # Line 1
    for num in nums:                   # Line 2
        if num in seen:                # Line 3
            return True                # Line 4
        seen.add(num)                  # Line 5
    return False                       # Line 6
```
Line 1: seen = set()

Creates an empty set data structure to track numbers we've already encountered
Why a set: Sets provide O(1) average lookup time - we can check "have I seen this number before?" almost instantly
Why not a list: Lists require O(n) time to search through every element - much slower!
Why write it this way: set() is the most efficient data structure for membership testing
Memory trade-off: We use extra memory to store seen numbers, but gain massive speed improvements.


2Sum Bruteforce:

```
def two_sum_brute_force(nums, target):
    """Brute force solution - check all pairs"""
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return []
```

```
def lengthOfLongestSubstring(s):
    seen = set()
    left = 0
    max_len = 0

    for right in range(len(s)):
        while s[right] in seen:
            seen.remove(s[left])
            left += 1
        seen.add(s[right])
        max_len = max(max_len, right - left + 1)

    return max_len
```
```
def threeSum(nums):
    nums.sort()
    res = []

    for i in range(len(nums) - 2):
        # Skip duplicates for the first number
        if i > 0 and nums[i] == nums[i - 1]:
            continue

        left, right = i + 1, len(nums) - 1
        while left < right:
            total = nums[i] + nums[left] + nums[right]

            if total < 0:
                left += 1
            elif total > 0:
                right -= 1
            else:
                res.append([nums[i], nums[left], nums[right]])

                # Skip duplicates for the second number
                while left < right and nums[left] == nums[left + 1]:
                    left += 1
                # Skip duplicates for the third number
                while left < right and nums[right] == nums[right - 1]:
                    right -= 1

                left += 1
                right -= 1

    return res

# Example run
print(threeSum([-1, 0, 1, 2, -1, -4]))
```

```

from typing import List

def merge(intervals: List[List[int]]) -> List[List[int]]:
    intervals.sort(key=lambda x: x[0])  # sort by start
    merged = []
    for s, e in intervals:
        if not merged or s > merged[-1][1]:
            merged.append([s, e])
        else:
            merged[-1][1] = max(merged[-1][1], e)
    return merged
```

```
Sliding window:
Old sum = 4 + 2 + 1 = 7
New sum = 2 + 1 + 7 = ?


New sum = (4 + 2 + 1) - 4 + 7
New sum = Old sum - element_leaving + element_entering
New sum = 7 - 4 + 7 = 10

approach:
Start: [2,1,5] → sum = 8
Slide: Remove 2, Add 1 → [1,5,1] → sum = 8-2+1 = 7
Slide: Remove 1, Add 3 → [5,1,3] → sum = 7-1+3 = 9  
Slide: Remove 5, Add 2 → [1,3,2] → sum = 9-5+2 = 6
Maximum = 9
```
```
def containsDuplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```
```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        f = {}
        for c in s:
            if c in f:
                f[c] += 1
            else:
                f[c] = 1
        
        for c in t:
            if c not in f: return False
            elif f[c] == 1: del f[c]
            else: f[c] -= 1
        
        return not f

```

```
def length_of_longest_substring(s):
    char_set = set()
    left = 0
    max_length = 0
    
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)
    
    return max_length

# Example usage
s = "abcabcbb"
print(length_of_longest_substring(s))  # Output: 3
```
