## 169. Majority Element

##### Medium | C++ Code Solution Explanation | Array | Boyer-Moore Voting Algorithm

[Link to the Problem](https://leetcode.com/problems/majority-element/)

#### Problem

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

#### Solution

- If by some way we add +1 on getting same element and -1 on getting different element.
- The majority element in the end will make the sum more than 0.
- On getting zero as count we update the candidate of majority element.
- If we had some way of counting instances of the majority element as +1+1 and instances of any other element as -1−1, summing them would make it obvious that the majority element is indeed the majority element.
- The element in the last is the majority element.

#### Code

```
int majorityElement(vector<int>& nums) {
        int c=1;
        int can = nums[0];

        for(int i=1; i<nums.size(); i++){


            if(c==0)can=nums[i];

            c+=(nums[i]==can? 1 : -1);

        }
        return can;

    }
```
