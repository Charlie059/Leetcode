
# 剑指 Offer 51. 数组中的逆序对  LCOF - 数组中的逆序对

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Binary Indexed Tree-树状数组-blue.svg">   <img src="https://img.shields.io/badge/Segment Tree-线段树-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Binary Search-二分查找-blue.svg">   <img src="https://img.shields.io/badge/Divide and Conquer-分治-blue.svg">   <img src="https://img.shields.io/badge/Ordered Set-有序集合-blue.svg">   <img src="https://img.shields.io/badge/Merge Sort-归并排序-blue.svg">  


## Description - 题目描述

### EN:
English description is not available for the problem. Please switch to Chinese.

### ZH-CN:
<p>在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入</strong>: [7,5,6,4]
<strong>输出</strong>: 5</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 数组长度 &lt;= 50000</code></p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/shu-zu-zhong-de-ni-xu-dui-lcof/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/shu-zu-zhong-de-ni-xu-dui-lcof/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 172 ms | 43.4 MB | 2022/11/16 16:11 |

```cpp

class Solution {
public:
    int reversePairs(vector<int>& nums) {
        int n = nums.size();
        vector<int> tmp(n);
        return mergeSort(0, n - 1, nums, tmp);
    }

    int mergeSort(int l, int r, vector<int>& nums, vector<int>& tmp){
        if(l >= r) return 0;

        int m = r + ((l - r) >> 2);

        int res = mergeSort(l, m, nums, tmp) + mergeSort(m + 1, r, nums, tmp);


        int i = l, j = m + 1;
        for(int k = l; k <= r; k++) tmp[k] = nums[k];
        for(int k = l; k <= r; k++){
            if(i == m + 1){
                nums[k] = tmp[j++];
            }else if(j == r + 1){
                nums[k] = tmp[i++];
            }else if(tmp[i] <= tmp[j]){
                nums[k] = tmp[i++];
            }else{
                nums[k] = tmp[j++];
                res += m - i + 1;
            }
        }

        return res;
      
    }
};

```
## My Notes - 我的笔记


No notes

