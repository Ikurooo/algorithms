# Question
Given an array of integers citations where citations[i] is the number of
citations a researcher received for their ith paper, return the researcher's
h-index.

According to the definition of <a href="https://en.wikipedia.org/wiki/H-index">h-index on Wikipedia</a>: The h-index is defined as
the maximum value of h such that the given researcher has published at least h
papers that have each been cited at least h times.

# Intuition
For us to be able to find an index that is greater than the amount of books that have at least that many citations we need some sort of order in the array, so that we can compare the number of citations to the number of books that have been cited at least n times, n being the index in the sorted array.

# Approach
we use the built in python functions sorted(reverse=True) and enumerate() -> to get the index of each book in the list and a simple if statement to check if the book has a lower value than the index; if it does we break out; if we reach the end of the loop that means all books fit the criteria and so we return the length of the list.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n log n) + O(n)*</span>
 which simplifies to <span style="font-family: cursive;">*O(n log n)*</span>

- Space complexity:
In most cases sorting functions sort in-place HOWEVER the python sorted() function (not to be confused with the .sort() function) returns a new sorted list giving us a final space complexity of <span style="font-family: cursive;">*O(n)*</span>

# Code
```python
class Solution:
    def hIndex(self, citations: List[int]) -> int:
        for i, num in enumerate(sorted(citations, reverse=True)):
            if num <= i:
                return i
        return len(citations)
```