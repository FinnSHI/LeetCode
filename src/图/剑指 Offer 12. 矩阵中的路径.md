# [剑指 Offer 12. 矩阵中的路径](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/)

## 题目

给定一个 `m x n` 二维字符网格 `board` 和一个字符串单词 `word` 。如果 `word` 存在于网格中，返回 `true` ；否则，返回 `false` 。

```
示例 1：
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true

示例 2：
输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
```

## 思路

图算法的深度优先遍历（DFS） + 剪枝



## 代码

```java
/* dfs + 剪枝 */
class Solution {

    public boolean exist(char[][] board, String word) {
        // String 变成 char 数组
        char[] words = word.toCharArray();
        // 确定过的字符
        for(int i=0; i<board.length; i++) {
            for(int j=0; j<board[0].length; j++) 
                if(dfs(board, words, i, j, 0)) return true; 
        }
        return false;
     }

    
    /*
    * 深度优先搜索遍历图
    */
    public boolean dfs(char[][] board, char[] words, int i, int j, int k) {
        if(i < 0 || j < 0 || i >= board.length || j >= board[0].length || board[i][j] != words[k]) return false;
        if(k == words.length-1) return true;
        board[i][j] = '\0';
        boolean res =
                (dfs(board, words, i, j+1, k+1)
                        || dfs(board, words, i+1, j, k+1)
                        || dfs(board, words, i, j-1, k+1)
                        || dfs(board, words, i-1, j, k+1));
        board[i][j] = words[k];
        return res;
    }
}
```



## 复杂度

K为字符串的长度

时间复杂度：$O(3^K*M*N)$ ：每次递归时，除去来的方向，还有3个方向去递归，M*N是矩阵的大小。

空间复杂度：$O(K)$  