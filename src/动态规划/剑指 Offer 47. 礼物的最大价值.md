# [剑指 Offer 47. 礼物的最大价值](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

## 题目

在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？

 

```
示例 1:

输入: 
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 12
解释: 路径 1→3→5→2→1 可以拿到最多价值的礼物
```

## 思路

先考虑用图的DFS去做，结果超出时间限制了。

![image-20220125142845837](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202201251428940.png)



看了大佬的解法，原来需要**动态规划**

1. 对于当前节点 $(i,j)$ 来说，上一个节点只有可能来自于上方 $(i-1,j)$ 或者左边 $(i, j-1)$

2. 因此，得到转移方程为：

   $f(i,j) = max[f(i-1,j),f(i,j-1)] + grid[i][j]$

动态规划：

- 状态定义：动态规划矩阵 $dp[i][j]$，保存当前礼物最大值

- 转移方程：

  ![image-20220125144049346](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202201251440381.png)

- 初始状态：$i=0,j=0$，$dp[0][0]=grid[0][0]$

- 返回值：

## 代码

```java
// /* dfs： 超出时间限制 */
// class Solution {
//     Set<Integer> values = new HashSet<>();
//     public int maxValue(int[][] grid) {
//         dfs(grid, 0, 0, 0);
//         return Collections.max(values);
//     }

    
//     public void dfs(int[][] grid, int i, int j, int value) {
//         if(i < 0 || j < 0 || i >= grid.length || j >= grid[0].length) {
//             return;
//         }
//         value += grid[i][j];
//         // 到达右下角
//         if(i == grid.length-1 && j == grid[0].length-1)
//             values.add(value);
//         //先往右，再往下
//         dfs(grid, i, j+1, value);
//         dfs(grid, i+1, j, value);
//     }
// }

class Solution {
    int[][] dp;
    public int maxValue(int[][] grid) {
        int row = grid.length;
        int volumn = grid[0].length;
        dp = new int[row][volumn];
        dp[0][0] = grid[0][0]; 
        for(int i = 0; i < row; i++)
            for(int j = 0; j < volumn; j++) {
                dp[i][j] = (i == 0 && j != 0) ? grid[i][j] + dp[i][j-1] : dp[i][j];
                dp[i][j] = (i != 0 && j == 0) ? grid[i][j] + dp[i-1][j] : dp[i][j];
                dp[i][j] = (i != 0 && j != 0) ? grid[i][j] + Math.max(dp[i][j-1], dp[i-1][j]) : dp[i][j];
            }

        return dp[row-1][volumn-1];
    }
}
```

## 复杂度

时间复杂度：$O(MN)$

空间复杂度：$O(MN)$   如果在原地修改，则只需要占用 $O(1)$ 复杂度

