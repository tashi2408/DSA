## 53. Maximum Subarray

##### Medium | C++ Code Solution Explanation | Array | Kadane

[Link to the Problem](https://leetcode.com/problems/maximum-subarray/)

#### Problem

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

#### Solution

- There are only 2 cases that the element is greater of the element + sum so far is greater.
- We need to check adding an element to the sum so far (elements encountered in the array so far) is greater than the element itself.
- If the sum is greater we go with it else we drop the sum do far and start the new sum from that element.

Why take in consideration the sum of the continuous array so far if the value of single element is greater?

#### Code

```
int maxSubArray(vector<int>& nums) {
        int a= nums[0];
        int b=nums[0];

        for(int i=1; i<nums.size(); i++){
            a= max(nums[i], a+nums[i]);
            b=max(b, a);

        }

        return b;
    }
```
