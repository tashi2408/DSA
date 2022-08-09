## 823. Binary Tree with Factors

##### Medium | C++ Code Solution Explanation | DP

[Link to the Problem](https://leetcode.com/problems/binary-trees-with-factors/)

#### Problem

Given an array of unique integers, arr, where each integer arr[i] is strictly greater than 1.

We make a binary tree using these integers, and each number may be used for any number of times. Each non-leaf node's value should be equal to the product of the values of its children.

Return the number of binary trees we can make. The answer may be too large so return the answer modulo 109 + 7.

#### Solution

- It is similar to the question where we were given to find the target sum or product(using three elements).
- Here the target is also an element and the 2 number forming the product are also in the array.
- If we sort the array we will always know that the product forming elements have occured before.
- We will pick an element and form the pair which will result in the product.
- We can do that using two other loops.
- But if we make a hashmap we will need one loop to find the element and the other can be found by searching the hash map.

**For example:**

`[2, 5, 10]` if `nums[i] = 10` then we loop to find `num[i]%num[j]==0` and then `map[num[i]/num[j]]` now we know that as 2, 5 form sub trees. So, elements under 2, 5 will also be under 10.

- As we can see subproblems forming we will keep hashmap as the dp array.
- Why make a different array if are not using the key value pair in the map?

- The `values` in the hashmap will give number of elements the tree with `key` as the root will have.
- The value will be equal to the elements the factors will having in their tree.

```C++
dp[10] = dp[10] + dp[2]+ dp[10/2];
```

Each element can also form a tree with root node only so we set `dp[10]=1` and add that as well.

#### Code

```
int numFactoredBinaryTrees(vector<int>& nums) {
        int n = nums.size();
        sort(nums.begin(), nums.end());
        map<int, long>dp;
        int mod = 1000000007;
        int sum=0;
        for(int i=0; i<n; i++){
            dp[nums[i]]=1;
            for(int j=0; j<i; j++){
                if(nums[i]%nums[j]==0){
                    dp[nums[i]]= (dp[nums[i]]%mod+ (dp[nums[i]/nums[j]]%mod)*(dp[nums[j]]%mod)%mod)%mod;
                }
            }
            sum=(dp[nums[i]]%mod + sum%mod)%mod;
        }
        return sum;
    }
```
