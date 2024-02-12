# Question
Given an array of intervals where intervals[i] = [starti, endi],
merge all overlapping intervals, and return an array of the non-overlapping
intervals that cover all the intervals in the input.

# Intuition
We need some sort of order between the intervals, so that it is easier
to tell which intervals end where other intervals start. -> Sort the
intervals by their start in ascending order.

# Approach
We sort the intervals as mentioned above using the .sort() function and
using a lambda we pass in the start value to the sorting function. After
that we set the start of the current merged interval as the first 0th
element of our first interval. We iterate through the array and keep
updating the end value of our merged interval, by choosing the max of 
the current last value 'part2' and the last value of the current interval.
We do the aforementioned step up until we hit an interval where the start 
value is greater than the current end value 'part2' at which point we push
the merged interval to the merged array and start the whole process all over.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we only iterate through the array once.

- Space complexity:
<span style="font-family: cursive;">*O(n)*</span> Since .sort() sorts in-place however in the worst case we need to
store the same amount of elements as in the original array

# Code
```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda x: x[0])
    
        if len(intervals) <= 1:
            return intervals

        merged = []
        part1 = intervals[0][0]
        part2 = intervals[0][1]
        for i in range(1, len(intervals)):
            if intervals[i][0] <= part2:
                part2 = max(intervals[i][1], part2)
            else:
                merged.append([part1, part2])
                part1 = intervals[i][0]
                part2 = intervals[i][1]
        merged.append([part1, part2])
        return merged
```