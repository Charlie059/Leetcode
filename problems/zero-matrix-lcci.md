
# 面试题 01.08. Zero Matrix LCCI - 零矩阵

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">  


## Description - 题目描述

### EN:
<p>Write an algorithm such that if an element in an MxN matrix is 0, its entire row and column are set to 0.</p>

<p>&nbsp;</p>

<p><strong>Example 1: </strong></p>

<pre>
<strong>Input: </strong>
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
<strong>Output: </strong>
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]
</pre>

<p><strong>Example 2: </strong></p>

<pre>
<strong>Input: </strong>
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
<strong>Output: </strong>
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
</pre>


### ZH-CN:
<p>编写一种算法，若M × N矩阵中某个元素为0，则将其所在的行与列清零。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
<strong>输出：</strong>
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
<strong>输出：</strong>
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
</pre>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/zero-matrix-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/zero-matrix-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 11.8 MB | 2022/09/29 15:38 |

```cpp

class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        const int m = matrix.size();
        const int n = matrix[0].size();

        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(matrix[i][j] == 0) matrix[i][j] = INT_MIN / 2;
            }
        }

        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(matrix[i][j] == INT_MIN / 2){
                    // Replace row
                        for(int r = 0; r < m; r++){
                            if(r != i && matrix[r][j] != INT_MIN / 2) matrix[r][j] = 0;
                        }

                    // Replace col
                        for(int c = 0; c < n; c++){
                            if(c != j && matrix[i][c] != INT_MIN / 2) matrix[i][c] = 0;
                        }                        
                }
            }
        }
        
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(matrix[i][j] == INT_MIN / 2) matrix[i][j] = 0;
            }
        }

    }
};

```
## My Notes - 我的笔记


No notes

