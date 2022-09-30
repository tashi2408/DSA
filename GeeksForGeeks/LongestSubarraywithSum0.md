## Largest subarray with 0 sum

##### Easy | C++ Code Solution Explanation | Array

[Link to the Problem](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

#### Problem

Given an array having both positive and negative integers. The task is to compute the length of the largest subarray with sum 0.

Input:
N = 8
A[] = {15,-2,2,-8,1,7,10,23}

Output: 5

Explanation: The largest subarray with sum 0 will be -2 2 -8 1 7.

#### Solution

- Subarray with sum 0 can start at any index and end at any index.
- If we have the val of sum till start and sum till end
- `sum[start index]` and `sum[end index]`
- Then `sum[end index] - sum[start index]` will give us the some between two points in an array.

- Also, if we have sum[i]==sum[j] i!=j then it means all element between them add to give 0.
- So we keep on calculating the sum and checking that do we have same sum earlier.
- we can use map to store the sum and the index where same sum was found.

#### Code

```
int maxLen(vector<int>&A, int n)
    {
        // Your code here
        map<int, int>sum;
        long long s=0;
        int res=0;
        for(int i=0; i<A.size(); i++){

            s+=A[i];
            if(s==0)res=max(res, i+1);
            if(A[i]==0)res= max(res, 1);
            if(sum.count(s)){
                res= max(res, i-sum[s]);
            }else{
                sum[s]=i;
            }

        }

        return res;
    }
```
