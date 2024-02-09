# Question
You are given an array prices where prices[i] is the price of a given stock
on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and
choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot
achieve any profit, return 0.

# Intuition
we can be greedy since it is guaranteed that the stock prices will never fall
below 0, and so we can always choose the lowest possible value to subtract from
each subsequent stock price.

# Approach
Using a two pointer algorithm where the left pointer keeps track of the current
minimum and for each value in the array comparing the difference between the 
element at the current position and the one at the left pointer.

# Complexity
- Time complexity:
<span style="font-family: cursive;">*O(n)*</span> Since we iterate over the array exactly once.

- Space complexity:
<span style="font-family: cursive;">*O(1)*</span> Since we don't assign any extra arrays to store the best result for each position.

# Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        globalMax = 0
        l = 0

        for i in range(len(prices)):
            if prices[i] < prices[l]:
                l = i
            globalMax = max(globalMax, prices[i] - prices[l])
        return globalMax
```