# Question
You are given two integer arrays nums1 and nums2, sorted in non-decreasing order,
and two integers m and n, representing the number of elements in nums1 and nums2
respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be
stored inside the array nums1. To accommodate this, nums1 has a length of m + n,
where the first m elements denote the elements that should be merged, and the
last n elements are set to 0 and should be ignored. nums2 has a length of n.

# Intuition
Given that the two arrays are already sorted and that the first array has enough space
to contain ALL the elements of the second one we can pick and choose elements from the
last number in both arrays and start putting them and the true end of the first one.

# Approach
To achieve this we require 2+1 pointers where p1 and p2 point to the last unmerged
element in the arrays and endpointer pointing to the last unused spot of the array.
For each iteration of the while loop we compare the two elements in the two arrays
and pick the larger one, put it at the position of the endpointer, then decrement the
endpointer as well as the pointer of the array we just took the element from. Additionally,
after the first while loop there could be the case that there's still elements left in the
second array, so we need to put each of them into the first one.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(m + n)*</span> Since we only iterate through each array once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't create any additional arrays to store the elements.

# Code
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        p1 = m - 1  # since n is the number of elements and the array is 0 indexed
        p2 = n - 1  # since m is the number of elements and the array is 0 indexed
        endpointer = m + n - 1 # verbatim

        while p2 >= 0 and p1 >= 0:
            if nums1[p1] > nums2[p2]:
                nums1[endpointer] = nums1[p1]
                p1 -= 1
            else:
                nums1[endpointer] = nums2[p2]
                p2 -= 1
            endpointer -= 1
        
        while p2 >= 0:
            
            nums1[endpointer] = nums2[p2]
            p2 -= 1
            endpointer -= 1
```