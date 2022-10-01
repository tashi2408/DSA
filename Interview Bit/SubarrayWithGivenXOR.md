## Subarray with given XOR

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://www.interviewbit.com/problems/subarray-with-given-xor/)

#### Problem

Given an array of integers A and an integer B.

Find the total number of subarrays having bitwise XOR of all elements equals to B.

Example Input
Input 1:

A = [4, 2, 2, 6, 4]
B = 6
Input 2:

A = [5, 6, 7, 8, 9]
B = 5

Example Output
Output 1:

4
Output 2:

2

Explanation 1:

The subarrays having XOR of their elements as 6 are: [4, 2], [4, 2, 2, 6, 4], [2, 2, 6], [6]

Explanation 2:

The subarrays having XOR of their elements as 5 are: [5] and [5, 6, 7, 8, 9]

#### Solution

- It's like 2 sum.
- We traverse and while traversing check whether a single element is equal to target XOR.
- Also, We check xor till now is = to target XOR.
- We will store the XOR at each index in the map.
- At each index we XOR the current XOR with the target and search the Value in map.
- We add the number of times the value has been encountered to our answer.

#### Code

```
int Solution::solve(vector<int> &A, int B) {
    unordered_map<int, int>m;
    int x =0;
    int c=0;

    for(int n: A){

        x^=n;
        if(x==B)c++;
        if(m.count(x^B))c+=m[x^B];
        m[x]++;
    }

    return c;

}
```
