# Burst Ballons
## Problem
Given n balloons, indexed from 0 to n-1. Each balloon is painted with a number on it represented by array nums. You are asked to burst all the balloons. If the you burst balloon i you will get nums[left] * nums[i] * nums[right] coins. Here left and right are adjacent indices of i. After the burst, the left and right then becomes adjacent.

Find the maximum coins you can collect by bursting the balloons wisely.

## Analysis
Use DP to solve this problem

dp[i][j] means: the maximum coins you can collect by bursting the ballons from i to j

then dp[i][j]: loop along the i to j, make each one the last to burst, then :

```
for k in i-j:
dp[i][j]= max{dp[i][j], dp[i-1][k-1]+nums[left-1]*nums[k]*nums[right+1]*dp[k+1][right]}
```

then we can return dp[0][len-1]

```java
public class Solution {
public int maxCoins(int[] nums) {
    if (nums == null || nums.length == 0) return 0;
    
    int[][] dp = new int[nums.length][nums.length];
    for (int len = 1; len <= nums.length; len++) {
        for (int start = 0; start <= nums.length - len; start++) {
            int end = start + len - 1;
            for (int i = start; i <= end; i++) {
                int coins = nums[i] * getValue(nums, start - 1) * getValue(nums, end + 1);
                coins += i != start ? dp[start][i - 1] : 0; // If not first one, we can add subrange on its left.
                coins += i != end ? dp[i + 1][end] : 0; // If not last one, we can add subrange on its right
                dp[start][end] = Math.max(dp[start][end], coins);
            }
        }
    }
    return dp[0][nums.length - 1];
}

private int getValue(int[] nums, int i) { // Deal with num[-1] and num[num.length]
    if (i < 0 || i >= nums.length) {
        return 1;
    }
    return nums[i];
}
}
```
