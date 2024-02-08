# Question
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.

# Intuition
Since we cannot assume that this element exists we need to count the occurrence of
each element and if the array had some order we wouldn't have to iterate over the
array for each element in it to find all those that equal it.

# Approach
Using the built-in python .sort() function to sort the array and then iterate over
the array using a left and right pointer, the former keeping track of the current
element being counted and the latter checking for each occurrence of that element.
If we find an element like this we append it to the list of results.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n log n) + O(n)*</span> Since we sort and then iterate over the array.
Which simplifies to
<span style="font-family: cursive;">*O(n log n)*</span>

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since in the worst case we need 3 extra 'slots' for the list.

# Code
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        nums.sort()
 
        result = []
        n = len(nums)
        
        # Use a two-pointer approach to find elements that occur at least n/3 times
        left, right = 0, 0
        while right < n:
            while right < n and nums[right] == nums[left]:
                right += 1
            
            # Check if the frequency of the current element is at least n/3
            if right - left > n // 3:
                result.append(nums[left])
            
            left = right
        
        return result
```