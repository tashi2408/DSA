## 1220. Count Vowels Permutation

##### Hard | C++ Code Solution Explanation | Dynamic Programming

[Link to the Problem](https://leetcode.com/problems/count-vowels-permutation/)

#### Problem

Given an integer n, your task is to count how many strings of length n can be formed under the following rules:

- Each character is a lower case vowel ('a', 'e', 'i', 'o', 'u')
- Each vowel 'a' may only be followed by an 'e'.
- Each vowel 'e' may only be followed by an 'a' or an 'i'.
- Each vowel 'i' may not be followed by another 'i'.
- Each vowel 'o' may only be followed by an 'i' or a 'u'.
- Each vowel 'u' may only be followed by an 'a'.

Since the answer may be too large, return it modulo 10^9 + 7.

#### Solution

let the vowels be denoted as numbers

- a = 0
- e = 1
- i = 2
- o = 3
- u = 4

1. We will make two vectors `prev`,` cur`.
2. `prev` will store the number of strings that are ending with each vowel and will be used to calculate `cur`.
3. Values will be calculated from previous string using the rules mentioned.

For Example:

- The string of length ` n-1` can be appended with 'a' (or end with 'a') to make length `n` only if when string of length `n-1` end with 'e' or 'i' or 'u',
  `cur[a]= prev[e] + prev[i]+ prev[u];`
- Similarly we can calculate for other vowels.

#### Code

```
int countVowelPermutation(int n) {

        vector<int>prev(5, 1);
        vector<int>cur(5, 1);

        int sum =0, mod=1000000007;

        for(int i=1; i<n; i++){
            cur[0]= ((prev[1]%mod + prev[2]%mod)%mod + prev[4]%mod)%mod;
            cur[1]=(prev[0]%mod + prev[2]%mod)%mod;
            cur[2]= (prev[1]%mod + prev[3]%mod)%mod;
            cur[3]= prev[2]%mod;
            cur[4] = (prev[2]%mod + prev[3]%mod)%mod;
            prev = cur;
        }

        for(int i=0; i<5; i++){

            sum=((cur[i]%mod) + sum%mod)%mod;
        }

        return sum;
    }
```
