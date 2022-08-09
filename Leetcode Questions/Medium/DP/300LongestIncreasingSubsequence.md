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

- Traverse from left to right and maintain an array `sub` which contains elements of the longest increasing subsequence so far.
- Append to `sub` if we have `num[i]` greater than the last element of `sub`.
- If element is less than the last element then we can't append to `sub` cause it will no longer be in increasing order.
- We search for the just bigger element in `sub` using binary search.
- We replace th element with just bigger number. In this way we keep the maximum length same and also we can append numbers which lie in the range of replacing and replaced number.
- For Example: `[2, 6, 8]` next number is 3 so sub = `[2, 3, 8]`. We kept the length same and no need to maintain 2 subarray as sub array with smaller elements have more chance of forming a bigger length.
- The length of the `sub` after traversing the entire `num` is the answer.

#### Code

```
int binarySearch(vector<int>a, int m, int l, int r){
        int i=r, mid;
        while(l<=r){
            mid= (l+r)>>1;
            if(a[mid]==m)return -1;
            if(a[mid]>m){
                r=mid-1;
                i=mid;
            }else{
               l=mid+1;
            }
        }
        return i;
    }
    int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();
        vector<int>sub;
        sub.push_back(nums[0]);

        int j=0;
        for(int i=1; i<n; i++){
            if(nums[i]>sub[j]){
                sub.push_back(nums[i]);
                j++;
            }else if(nums[i]==sub[j]){
                continue;
            }else{

                int index = binarySearch(sub, nums[i], 0, j );

                if(index!=-1)
                sub[index]=nums[i];

            }
        }


        return sub.size();
    }

```
