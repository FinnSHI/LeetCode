# [剑指 Offer 12. 矩阵中的路径](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/)

## 题目

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

```
示例 1：

输入：m = 2, n = 3, k = 1
输出：3

示例 2：

输入：m = 3, n = 1, k = 0
输出：1
```

## 思路

DFS 或 BFS



## 代码

```java
class Solution {
    boolean[][] visited;
    int count = 0;

    public int movingCount(int m, int n, int k) {
        visited = new boolean[m][n];        
        dfs(0, 0, k);           
        return count;
    }

    // dfs
    // i: row
    // j: column
    public void dfs(int i, int j, int k) {
        int sumi = (i<9) ? i : this.getSum(i);
        int sumj = (j<9) ? j : this.getSum(j);

        // 越界情况:
        // 1.出界
        // 2.访问过了
        if(i < 0 || i >= visited.length || j < 0 || j >= visited[0].length || visited[i][j] == true || sumi + sumj > k) {
            return;
        }
        visited[i][j] = true;
        // 能走到该格子
        count++;
        // down
        dfs(i+1, j, k);
        // right
        dfs(i, j+1, k);
        // up
        dfs(i-1, j, k);
        // left
        dfs(i, j-1, k);
    }

    // 拆数
    public int getSum(int i) {
        int sum = 0;
        while(i != 0) {
            sum += i % 10;
            i /= 10;
        }
        return sum;
    }

} 
```



## 复杂度

时间复杂度：$O(M*N)$

空间复杂度：$O(M*N)$

