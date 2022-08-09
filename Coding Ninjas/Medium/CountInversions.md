## 53. Maximum Subarray

##### Medium | C++ Code Solution Explanation | Array | Kadane

[Link to the Problem](https://www.codingninjas.com/codestudio/problems/count-inversions_615?leftPanelTab=0)

#### Problem

Given an array of N integers, count the inversion of the array.
What is an inversion of an array? Definition: for all i & j < size of array, if i < j then you have to find pair (A[i],A[j]) such that A[j] < A[i].

#### Solution

- To count the inversion we need to find how many numbers greater we have encountered so far.
- If we sort the array so far then looking at the position of the element we can find out how many numbers are greater.
- Instead of making different array and sorting it again we can use merge sort.
- We divide it untill we get single elements and when merging we have 2 arrays `left` and `right`.
- We first element in `right` is smaller than first element in `left' it means it can form a pair with all remaining elememts `left`.
- So every time `right` element is smaller we add number of elements remaining in `left` to the count.
- `count` gives the number of inversion for the smaller right element.
- We add all the `count` to get final answer.

#### Code

```
#include <bits/stdc++.h>

long long merge(long long arr[],long long temp[],int left,int mid,int right)
{
    long long inv_count=0;
    int i = left;
    int j = mid;
    int k = left;
    while((i <= mid-1) && (j <= right)){
        if(arr[i] <= arr[j]){
            temp[k++] = arr[i++];
        }
        else
        {
            temp[k++] = arr[j++];
            inv_count = inv_count + (mid - i);
        }
    }

    while(i <= mid - 1)
        temp[k++] = arr[i++];

    while(j <= right)
        temp[k++] = arr[j++];

    for(i = left ; i <= right ; i++)
        arr[i] = temp[i];

    return inv_count;
}

long long merge_Sort(long long arr[],long long temp[],int left,int right)
{
    int mid;
    long long inv_count = 0;
    if(right > left)
    {
        mid = (left + right)/2;

        inv_count += merge_Sort(arr,temp,left,mid);
        inv_count += merge_Sort(arr,temp,mid+1,right);

        inv_count += merge(arr,temp,left,mid+1,right);
    }
    return inv_count;
}


long long getInversions(long long *arr, int n){
    // Write your code here.
    long long temp[n];
    return merge_Sort(arr,temp, 0, n-1);
}
```
