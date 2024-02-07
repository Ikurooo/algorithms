# Question
Given an integer array nums and an integer val, remove all occurrences of val in
nums <a href="https://en.wikipedia.org/wiki/In-place_algorithm">in-place</a>.
The order of the elements may be changed. Then return the number of elements in
nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get
accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements
which are not equal to val. The remaining elements of nums are not important as
well as the size of nums. 

Return k.


# Intuition
Since overwriting any elements isn't prohibited we can just keep track of the elements
(using a slow pointer) that we can overwrite with the values at the fast pointer; the
fast pointer being just the for-loop iterator

# Approach
Using a for-loop to iterate over each element of the array and checking if it does NOT
equal the 'val', and if so then we copy the num at the fast pointer increment and
the slow pointer.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we iterate over the array only once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't create any additional arrays to store the elements.

# Code
```python
class Solution:
    def removeElement(self, nums, val):
        slow = 0
        for num in nums:
            if num != val:
                nums[slow] = num
                slow += 1
        return slow
```