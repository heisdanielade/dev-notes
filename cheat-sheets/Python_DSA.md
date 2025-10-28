# Useful Code Snippets
**DSA Toolkit for LeetCode.** A curated collection of highly reusable Python code snippets for common patterns and data structures (Heaps, Sets, Frequency Maps) to optimize problem-solving speed.

## Count Frequency of Items

a. Using `Counter`

```python
from collections import Counter

nums: List[int] = [1,7,3,1,8,4,2,9,1]

freq_map = Counter(nums)

# Most concise, readable, and idiomatic for counting.
```

b. Manual dictionary with `if` check

```python
freq_map = {}

for n in nums:
    if n not in freq_map:
        freq_map[n] = 0
    freq_map[n] += 1

# Verbose, but explicit. Works in all Python versions.
```

c. Using `defaultdict`

```python
from collections import defaultdict

freq_map = defaultdict(int)

for n in nums:
    freq_map[n] += 1

# Automatically initializes missing keys to 0
```

d. Dictionary with `.get()`

```python
freq_map = {}

for n in nums:
    freq_map[n] = freq_map.get(n, 0) + 1

# Slightly more compact than method b.
```

## Basic Array/List Operations

```python
from typing import List

arr: List[int] = [5, 2, 9, 1, 5]

# Sorting: In-place sort (modifies the original list)
arr.sort()
# arr is now [1, 2, 5, 5, 9]

# Sorting: Returns a new sorted list (original is unchanged)
sorted_arr = sorted(arr)

# Reversing: In-place reverse
arr.reverse()

# Initializing a list of a fixed size with a default value (e.g., for DP)
N = 5
dp_table = [0] * N  # [0, 0, 0, 0, 0]

# Initializing a 2D array (for matrices, DP tables, or grids)
ROWS, COLS = 3, 4
matrix = [[0] * COLS for _ in range(ROWS)]

# IMPORTANT: Use a list comprehension to avoid having rows share the same inner list object.
```

## String Reversal

```python
s: str = "hello"

# Method 1: Using slicing (most Pythonic)
reversed_s = s[::-1]  # "olleh"

# Method 2: Using join and reversed() (useful for list of strings/characters)
reversed_s_join = "".join(reversed(s)) # "olleh"

# Reversing a list of words
words: List[str] = ["the", "quick", "brown"]
words.reverse() # ["brown", "quick", "the"]
```

## Two Pointers Technnique

```python
from typing import List

def check_palindrome(s: str) -> bool:
    """Checks if a string is a palindrome using two pointers."""
    left, right = 0, len(s) - 1
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True

def two_sum_sorted(nums: List[int], target: int):
    """Finds two numbers in a sorted array that sum to a target."""
    left, right = 0, len(nums) - 1
    while left < right:
        current_sum = nums[left] + nums[right]
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1  # Need a larger sum
        else:
            right -= 1 # Need a smaller sum
    return []
```

## Sliding Window Pattern

```python
from typing import List

def max_subarray_size_k(nums: List[int], k: int) -> int:
    """Finds the maximum sum of a contiguous subarray of size k."""
    if not nums or k > len(nums):
        return 0

    max_sum = current_sum = sum(nums[:k])

    # Slide the window from index k to the end
    for i in range(k, len(nums)):
        # Add the new element (i) and subtract the element that fell off (i - k)
        current_sum = current_sum - nums[i - k] + nums[i]
        max_sum = max(max_sum, current_sum)

    return max_sum
```

## Set Operations

```python
from typing import List

list_a: List[int] = [1, 2, 3, 4]
list_b: List[int] = [3, 4, 5, 6]

set_a = set(list_a)
set_b = set(list_b)

# Intersection: Elements common to both
intersection = set_a.intersection(set_b) # {3, 4}
# Shorter operator syntax: intersection = set_a & set_b

# Union: All unique elements from both
union = set_a.union(set_b) # {1, 2, 3, 4, 5, 6}
# Shorter operator syntax: union = set_a | set_b

# Difference: Elements in A but not in B
difference = set_a.difference(set_b) # {1, 2}
# Shorter operator syntax: difference = set_a - set_b

# Check for existence (O(1) time complexity)
is_present = 3 in set_a # True
```

## Heap (Priority Queue)

```python
import heapq
from typing import List

# Min-Heap (default in Python)
min_heap: List[int] = [5, 1, 9, 4]
heapq.heapify(min_heap) # Converts the list into a heap in-place

# Push (O(log n))
heapq.heappush(min_heap, 2)

# Pop (O(log n)): Always removes and returns the smallest item
smallest = heapq.heappop(min_heap) # 1

# Max-Heap Simulation
# Python lacks a built-in Max-Heap. Simulate using negative values.
max_heap: List[int] = [-n for n in [5, 1, 9, 4]]
heapq.heapify(max_heap)

# Push to Max-Heap
heapq.heappush(max_heap, -10) # Push -10

# Pop from Max-Heap
largest = -heapq.heappop(max_heap) # Returns -9, negate to get 9
```
