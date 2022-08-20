## Sorted subsequence of size 3

##### Easy | C++ Code Solution Explanation | Array

[Link to the Problem](https://practice.geeksforgeeks.org/problems/sorted-subsequence-of-size-3/1)

#### Problem

Given an array A of N integers, find any 3 elements in it such that A[i] < A[j] < A[k] and i < j < k.

#### Solution

- For every element we need to find a element less than and greater than.
- So we maintain two arrays min array storing index of element less that a[i] and max array storing element greater than a[i].
- We maintain 2 variables to store index of min and max element.
- Since A[i] < A[j] && i< j
- We traverse from left to right updating the min index whenever we encounter a element less than element at min index
- At each position we compare a[min] with a[i] and update min array[i] with min index so far.
- If a[i] < a[min] then minarray[i]= -1 (means no less element).

Similarly,

- We update the max array. We traverse from right to left as A[k]> A[j] && k>j

Now,

- We linearly traverse and check at each element that whether we have a minimum and maximum element. If yes we add that triplet to result array.

#### Code

```
class Solution{
  public:
    vector<int> find3Numbers(vector<int> arr, int N) {
        // Your code here
        vector<int>mx(N, -1);
        vector<int>mn(N , -1);
        int n = N;

        int x = 0, y=n-1;

        for(int i=1; i<n; i++){
            if(arr[i]<=arr[x]){
                x=i;
            }else{
                mn[i]=x;
            }
        }

        for(int i=n-2; i>=0; i--){
            if(arr[i]>=arr[y]){
                y=i;
            }else{
                mx[i]=y;
            }
        }
        vector<int>res;

        for(int i=0; i<n; i++){
            if(mx[i]!=-1 && mn[i]!=-1){

                res= {arr[mn[i]], arr[i], arr[mx[i]]};
            }
        }
        return res;
    }
};
```
