
# 面试题 17.09. Get Kth Magic Number LCCI - 第 k 个数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Heap (Priority Queue)-堆（优先队列）-blue.svg">  


## Description - 题目描述

### EN:
<p>Design an algorithm to find the kth number such that the only prime factors are 3, 5, and 7. Note that 3, 5, and 7 do not have to be factors, but it should not have any other prime factors. For example, the first several multiples would be (in order) 1, 3, 5, 7, 9, 15, 21.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>k = 5

<strong>Output: </strong>9
</pre>


### ZH-CN:
<p>有些数的素因子只有 3，5，7，请设计一个算法找出第 k 个数。注意，不是必须有这些素因子，而是必须不包含其他的素因子。例如，前几个数按顺序应该是 1，3，5，7，9，15，21。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>k = 5

<strong>输出: </strong>9
</pre>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/get-kth-magic-number-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/get-kth-magic-number-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.3 MB | 2022/09/27 16:10 |

```cpp

class Solution {
public:
    int getKthMagicNumber(int k) {
        vector<int> factors = {3, 5, 7};
        unordered_set<int> hs;
        priority_queue<long, vector<long>, greater<long>> heap;
        hs.emplace(1L);
        heap.push(1L);
        int ans = 0;

        for(int i = 0; i < k; i++){
            long curr = heap.top();
            heap.pop();
            ans = curr;
            for(int factor: factors){
                long next = curr * factor;
                if(!hs.count(next)){
                    hs.emplace(next);
                    heap.push(next);
                }
            }
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

