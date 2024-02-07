# Question
Given an integer array nums sorted in non-decreasing order, remove the duplicates
in-place such that each unique element appears only once. The relative order of
the elements should be kept the same. Then return the number of unique elements
in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to
do the following things:

Change the array nums such that the first k elements of nums contain the unique
elements in the order they were present in nums initially. The remaining elements
of nums are not important as well as the size of nums.

Return k.


# Intuition
Keeping track of which element we can overwrite using a slow pointer and when an element
is found that is different from the current one at the slow pointer, incrementing it and
then swapping in the new element.

# Approach
Using a for-loop to iterate over each element of the array and checking if it does NOT
equal the 'val', and if so then we copy the num at the fast pointer increment
the slow pointer.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we iterate over the array only once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't create any additional arrays to store the elements.

# Code
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        slow = 0
        for num in nums:
            if num != nums[slow]:
                slow += 1
                nums[slow] = num
        return slow + 1
```