# Question
Given an integer array nums sorted in non-decreasing order, remove some duplicates
in-place such that each unique element appears at most twice. The relative order of
the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you
must instead have the result be placed in the first part of the array nums. More
formally, if there are k elements after removing the duplicates, then the first
k elements of nums should hold the final result. It does not matter what you leave
beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input
array in-place with O(1) extra memory.


# Intuition
Keeping track of which element we can overwrite using a slow pointer and when an element
is found that is different from the current one at the slow pointer, incrementing it and
then swapping in the new element. Additionally since elements can appear at most twice we
keep count so that we can store at most two if at least two of the same element is present.

# Approach
Using a for-loop to iterate over each element of the array and checking if it does NOT
equal the left adjacent element, and if so then we reset the counter. We also use a
variable count to increment the slow pointer when there is less than two elements in our
modified array and copy over elements to the position of the slow pointer if it is true.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we iterate over the array only once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't create any additional arrays to store the elements.

# Code
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        n = len(nums)
        
        if n <= 2:
            return n  # No need to process if the list has 2 or fewer elements
        
        slow = 1  # Start from the second element
        count = 1  # Counter for the current element
        
        for i in range(1, n):
            if nums[i] == nums[i - 1]:
                count += 1
            else:
                count = 1  # Reset the counter if the current element is different
            
            if count <= 2:
                nums[slow] = nums[i]
                slow += 1
        
        return slow
```