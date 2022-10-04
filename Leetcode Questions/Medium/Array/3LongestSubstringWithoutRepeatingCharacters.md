## 3. Longest Substring Without Repeating Characters

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#### Problem

Given a string s, find the length of the longest substring without repeating characters.

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

#### Solution

- We need to keep a track of all elements we have encountered so far.
- We use a vector of 256 with all initialized to -1. `map[256]`
- We keep two pointer one points to start of the substring and second to the rear end of the substring.
- We increment the rear end everytime and count the length at each iteration.
- At each iteration we alo check if the element has been encounter so far. `map[rear]!=-1`
- If the element is present after the starting point. Then we increment the start pointer to i+1. Else no change to start pointer.

#### Code

```
int lengthOfLongestSubstring(string s) {
        int l =0, r=0;
        vector<int>m(256, -1);
        int len =0;
        while(r<s.size()){
            if(m[s[r]]!=-1)
                l = max(m[s[r]]+1, l);
            m[s[r]]=r;
            len = max(len, r-l+1);
            r++;
        }

        return len;
    }
```
