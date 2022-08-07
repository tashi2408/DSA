## 48. Rotate Image

##### Medium | C++ Code Solution Explanation | Array

[Link to the Problem](https://leetcode.com/problems/maximum-subarray/)

#### Problem

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

![image](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)

#### Solution1

- Take the transpose of the matrix which bring the matrix column to row.
- Now atleast they are in same row.
- We observe that they are now just reverse of what we desire and hence we reverse it.

#### Code

```
void rotate(vector<vector<int>>& m) {
        for(int i=0; i<m.size(); i++){
            for(int j=0; j<i; j++){
                swap(m[i][j], m[j][i]);
            }
        }

        for(int i=0; i<m.size(); i++){
            reverse(m[i].begin(), m[i].end());
        }
    }
```

#### Solution2

```
/*
    Input
    1, 2, 3
    4, 5, 6
    7, 8, 9


    for-loop 1
    swap1               swap2               swap3
    1<->3               3<->9              9<->7

    3, 2, 1            9, 2, 1            7, 2, 1
    4, 5, 6    =>      4, 5, 6    =>      4, 5, 6
    7, 8, 9            7, 8, 3            9, 8, 3



    for-loop 2
    swap1              swap2              swap3
    2<->6              6<->8              8<->4

    7, 6, 1            7, 8, 1            7, 4, 1
    4, 5, 2    =>      4, 5, 2    =>      8, 5, 2
    9, 8, 3            9, 6, 3            9, 6, 3


    output
    7, 4, 1,
    8, 5, 2,
    9, 6, 3,
*/
```

#### Code

```
void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        int a = 0;
        int b = n-1;
        while(a<b){
            for(int i=0;i<(b-a);++i){
                swap(matrix[a][a+i], matrix[a+i][b]);
                swap(matrix[a][a+i], matrix[b][b-i]);
                swap(matrix[a][a+i], matrix[b-i][a]);
            }
            ++a;
            --b;
        }
    }
```
