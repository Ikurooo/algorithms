# Question
You are given an integer array prices where prices[i] is
the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock.
You can only hold at most one share of the stock at any time.
However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

# Intuition
For each stock in the array we need to check if it's left
neighbour is greater than itself to ensure that it is a local
maximum where we sell, and we set the left pointer to the right pointer
minus one to ensure that it is at the local minimum. This method
ensures that we always add the optimal amount to the total.

# Approach
Using two pointers l and r we iterate through the array checking for if
the above condition is met and if so we do the math and add it to the 
total. An edge-case we need to check for is if the right pointer has reached
the end, since it won't get automatically added to the sum due to how our 
while-loop condition works.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we only iterate through the array once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't create any additional arrays to store the best differences.

# Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)

        if n <= 1:
            return 0
        total_sum = 0
        left_pointer = 0

        for right_pointer in range(1, n):
            if prices[right_pointer - 1] > prices[right_pointer]:
                difference = prices[right_pointer - 1] - prices[left_pointer]
                total_sum += difference
                left_pointer = right_pointer

        difference = prices[right_pointer] - prices[left_pointer]
        total_sum += difference
        return total_sum
```