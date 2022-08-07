## 31. Next Permutation

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://leetcode.com/problems/next-permutation/)

#### Problem

A permutation of an array of integers is an arrangement of its members into a sequence or linear order.

- For example, for arr = [1,2,3], the following are considered permutations of arr: [1,2,3], [1,3,2], [3,1,2], [2,3,1].

The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

- For example, the next permutation of arr = [1,2,3] is [1,3,2].
- Similarly, the next permutation of arr = [2,3,1] is [3,1,2].
- While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.
  Given an array of integers nums, find the next permutation of nums.

The replacement must be in place and use only constant extra memory.

#### Solution

If we need to find the next permutation it means we need to find the number next in the dictionary order.

We start looking from the back and find the point where is digits stop ascending. It is the digit which will be replaced with the next bigger digit.

For Example:

- If number is `13542` then next is `14235`.
- The next changing point is where replacing the less significant digit with high significant digit will result in a bigger number. (That is 3)
- So, the next place will be where the higher significant digit is less than less significant digit.
- Now, we will find the next bigger digit we want the `3` to be replaced with.
- We will start from the back and look for the digit just bigger than `3` so that it remains in dictionary order.
- We find `4` and then replace it will `3`.
- Now, If we need the dictionary order then we need to sort then elements after the changing point but then were already in ascending order. (See from the step when when we looking for the changing point).
- So, just need to change it to descending.

![image](https://assets.leetcode.com/users/images/37c10db3-78c9-4dad-b7ac-3ccfb652d072_1659903108.7505944.png)

- In Loop1 we look for changing point.
- In the nested Loop2 we look for the number to replace.
- Then we reverse the array from the replacing point to the end.

#### Code

```
void nextPermutation(vector<int>& nums) {
        int i, j;
        for(i=nums.size()-2; i>=0; i--){

            if(nums[i]<nums[i+1] && i>=0){

                for(j=nums.size()-1; j>i; j--){
                    if(nums[j]>nums[i]){
                        int t=nums[j];
                        nums[j]=nums[i];
                        nums[i]=t;
                        break;
                    }
                }
                break;
            }
        }
        reverse(nums.begin() + i+1, nums.end());
    }
```
