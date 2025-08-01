# code-umbrella


```def contains_duplicate(nums):
    seen = set()                       # Line 1
    for num in nums:                   # Line 2
        if num in seen:                # Line 3
            return True                # Line 4
        seen.add(num)                  # Line 5
    return False                       # Line 6
```
Line 1: seen = set()

What happens: Creates an empty set data structure to track numbers we've already encountered
Why a set specifically: Sets provide O(1) average lookup time - we can check "have I seen this number before?" almost instantly
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
