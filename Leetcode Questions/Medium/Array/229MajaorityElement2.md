## 229. Majority Element II

##### Medium | C++ Code Solution Explanation | Array | Boyer-Moore Voting Algorithm

[Link to the Problem](https://leetcode.com/problems/majority-element-ii/)

#### Problem

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.

#### Solution

- According to maths there can be two elements who have count greater than n/3.
- So we maintain to variable n1, n2 and counts c1, c2.
- If c1=0 or c2=0 we update n1=nums[i] or n2=nums[i].
- After getting the nums we cross check that count of the n1, n2 by traversing the array again.
- If c1>nums.size()/3 push into res array
- If c2>nums.size()/3 push into res array

#### Code

```
vector<int> majorityElement(vector<int>& nums) {

        int c1=0, c2=0, n1=-1, n2=-1;

        for(int i=0; i<nums.size(); i++){
            if(n1==nums[i])c1++;
            else if(n2==nums[i])c2++;
            else if(c1==0){
                n1=nums[i];
                c1=1;
            }
            else if(c2==0){
                n2=nums[i];
                c2=1;
            }
            else{
                c1--;
                c2--;
            }
        }
        vector<int>ans;
        c1=0;
        c2=0;
        for(int i=0; i<nums.size(); i++){
            if(n1==nums[i])c1++;
            else if(n2==nums[i])c2++;
        }

        if(c1>nums.size()/3)ans.push_back(n1);
        if(c2>nums.size()/3)ans.push_back(n2);

        return ans;
    }
```
