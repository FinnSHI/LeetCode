## [剑指 Offer 63. 股票的最大利润](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

### 题目

假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

```
示例 1:
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
     
     
示例 2:
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```

### 思路

**动态规划**

- 状态定义： 设动态规划列表为$dp$，$dp[i]$ 是第 $i$ 天的利润最大值，$prices[i]$ 是第 $i$ 天的股票价格

- 转移方程： 

  $dp[i] = max(dp[i-1], prices[i] - min(prices[0: i-1])); $

  -  $dp[i]$ 是第 $i$ 天最大利润，其值等于前 $i-1$ 天的最大利润和第$i$天最大股票价减去前 $i-1$ 天股票最低价。
  - $min(prices[0: i-1])$ 只需要用一个常量来保存。

- 初始状态： $dp[0] = 0$，即首日利润为 $0$;

- 返回值： $dp[n - 1]$ ，其中 $n$ 为 $dp$ 列表长度。

   

### 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        // 动态规划
        /*
        * 状态定义： 设动态规划列表为dp，dp[i]是第i天的利润最大值，prices[i]是第i天的股票价格
        * 转移方程： dp[i] = max(dp[i-1], prices[i] - min(prices[i-1])); 
        *           dp[i]是当前
        * 初始状态： dp[0] = 0，即首日利润为 0;
        * 返回值： dp[n - 1] ，其中 n 为 dp 列表长度。
        */
        if(prices.length == 0) return 0;
        int dp = 0;// dp[i]和dp[i-1]
        int minPrice = prices[0]; // min(prices[0: i-1]) 
        
        for(int price : prices) {
            dp = Math.max(dp, price - minPrice);
            if(price < minPrice)
                minPrice = price;
        }

        return dp;    
    }
```



### 复杂度

时间复杂度：$O(n)$

空间复杂度：$O(1)$

