## 300. Longest Increasing Subsequence

##### Medium | C++ Code Solution Explanation | Dynamic Programming | Greedy

[Link to the Problem](https://leetcode.com/problems/longest-increasing-subsequence/)

#### Problem

Given an integer array nums, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].

#### Solution1 | Dynamic Programming

- Traverse the array from the left to right.
- We can take the element or not take the element.
- We can only include the element if the prev element is less.
- So we construct second loop to make sure that all previous element are less.
- If less we add the length of nums at that index.
- Now we have max length starting at each index.

#### Code

```
int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();

        vector<int>dp(n, 1);

        int m =1;
        for(int i=0; i<n; i++){
            for(int j=0; j<i; j++){
                if(nums[i]>nums[j] && dp[i]<dp[j]+1){
                    dp[i]=dp[j]+1;
                    m = max(m, dp[i]);
                }
            }
        }

        return m;
    }
```

#### Solution2 | Greedy

#### Code

```

```
