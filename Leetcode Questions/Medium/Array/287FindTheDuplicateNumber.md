## 287. Find the Duplicate Number

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://leetcode.com/problems/find-the-duplicate-number/)

#### Problem

Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.

There is only one repeated number in nums, return this repeated number.

You must solve the problem without modifying the array nums and uses only constant extra space.

#### Solution

- Traversing from left to right.
- We take the absolute value at every index. Let say x.
- Then we find `num[x]`. We change `num[x]` to `-num[x]`.

If we already have a negative `num[x]` then it means we have visited this index earlier.
It is only possible if x has been encountered before. It means x is the duplicate.

#### Code

```
int findDuplicate(vector<int>& nums) {
        int duplicate;
        for(int i=0; i<nums.size(); i++){
            int cur = abs(nums[i]);
            if(nums[cur]<0){
                duplicate = cur;
            }
            nums[cur]*=-1;
        }


        return duplicate;
    }
```
