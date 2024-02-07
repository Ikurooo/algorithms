# Question
Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may
assume that the majority element always exists in the array.

# Intuition
If the array was ordered, and we can assume that the element exists we could just
take the middle element from the array, and it would always be the majority element.
since if you have a line and have at least the half coloured in, and have a marker at
the midpoint of that line, the midpoint would always intersect with the coloured part
no matter where you slide it.

# Approach
Using the built-in .sort() function and python and whole division to get the index of
the element in the middle we return the element at that index.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n log n)*</span> Since the .sort() function takes <span style="font-family: cursive;">*O(n log n)*</span> time.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since the .sort() function sorts in place.

# Code
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        nums.sort()
        return nums[len(nums)//2]
```