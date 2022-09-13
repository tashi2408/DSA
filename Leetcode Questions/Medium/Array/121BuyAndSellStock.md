## 121. Best Time to Buy and Sell Stock

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

#### Problem

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

#### Solution

- We traverse from left to right and at every index we see the difference between the minimum value so far and A[i].
- So to keep track of minimum value we keep a variable and update the variable if A[i] < minval
- Now we see the difference and update the maxi which stores the max difference at each A[i].

#### Code

```
int maxProfit(vector<int>& prices) {
        int maxPro = 0;
    int minPrice = INT_MAX;

    for(int i = 0; i < prices.size(); i++){
        minPrice = min(minPrice, prices[i]);
        maxPro = max(maxPro, prices[i] - minPrice);
    }
    return maxPro;
    }
```
