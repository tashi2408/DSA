## 30. Substring with Concatenation of All Words

##### Hard | C++ Code Solution Explanation | Array | Kadane

[Link to the Problem](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

#### Problem

You are given a string s and an array of strings words of the same length. Return all starting indices of substring(s) in s that is a concatenation of each word in words exactly once, in any order, and without any intervening characters.

You can return the answer in any order.

#### Solution

- Because we need each word exactly once therefore we need to store the count of each word.
  We notice:
- Each word in the array is of the same length. so the string would contain letters = wordLen \* ArraySize

- To maintain a count of occurence we store each word in map.

- The result vector should contain all the indices and thats why we need traverse all the indices.
- At each index we take a string of wordLen store it in a map.
- If at the end of iteration the new map is equal to the old map then add the index to the result.

- During iteration if the count of the words exceed the total length then we break the loop.

#### Code

```
vector<int> findSubstring(string s, vector<string>& words) {
        vector<int> vec;
        unordered_map<string, int> umap;
        int count=0;
        for(auto w: words)      //map each word in words and it's freq
        {
            umap[w]++;
            count++;
        }
        int i, j, len, totLen;
        string  str;
        len = words[0].size();
        totLen = count*len;         // total length of all the words in words. each word is same length
        if(s.size()<totLen)
            return vec;
        for(i=0; i<=s.size()-totLen; i++)
        {
            count=0;
            unordered_map<string, int> newMap;
            for(j=i, count=0; j<s.size() && count<totLen; j+=len, count+=len)
            {
                str = s.substr(j, len);     //take substring of size len and map it to newMap, if the string does not exist in original umap, break the loop
                if(umap.find(str)!=umap.end())
                    newMap[str]++;
                else
                    break;
            }

            if(newMap==umap)        //compare old map umap to new map newMap, if match add index to result vector
                vec.push_back(i);
        }
        return vec;
    }
```
