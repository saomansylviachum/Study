# Cherry Pickup II
## Problem
Given a rows x cols matrix grid representing a field of cherries. Each cell in grid represents the number of cherries that you can collect.

You have two robots that can collect cherries for you, Robot #1 is located at the top-left corner (0,0) , and Robot #2 is located at the top-right corner (0, cols-1) of the grid.

Return the maximum number of cherries collection using both robots  by following the rules below:

From a cell (i,j), robots can move to cell (i+1, j-1) , (i+1, j) or (i+1, j+1).
When any robot is passing through a cell, It picks it up all cherries, and the cell becomes an empty cell (0).
When both robots stay on the same cell, only one of them takes the cherries.
Both robots cannot move outside of the grid at any moment.
Both robots should reach the bottom row in the grid.
 
## Analysis
This is a typical DP problem. We can use two different method to do this, first is top-down, DFS with record array. and second is the bottom up, which we don't need the recursive procedure, but iteration.

- First
```java
class Solution {
    public int cherryPickup(int[][] grid) {
        if(grid.length==0)return 0;
        int[][][] dp=new int[grid.length][grid[0].length][grid[0].length];
        for(int row=0;row<grid.length;row++)
        {
            for(int col1=0;col1<grid[0].length;col1++)
            {
                for(int col2=0;col2<grid[0].length;col2++)
                {
                    dp[row][col1][col2]=-1;
                }
            }
        }
        return helper(grid,0,0,grid[0].length-1,dp);
    }
    public int helper(int[][] grid, int row, int col1, int col2,int[][][] dp)
    {
        if(col1<0||col1>=grid[0].length||col2<0||col2>=grid[0].length)
            return 0;
        if(row==grid.length-1)
        {
            dp[row][col1][col2]=col1==col2?grid[row][col1]:grid[row][col1]+grid[row][col2];
            return dp[row][col1][col2];
        }
        if(dp[row][col1][col2]!=-1)
            return dp[row][col1][col2];
        int cur_max=0;
        cur_max=Math.max(cur_max,helper(grid,row+1,col1+1,col2,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1-1,col2,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1,col2,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1,col2-1,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1,col2+1,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1-1,col2+1,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1-1,col2-1,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1+1,col2-1,dp));
        cur_max=Math.max(cur_max,helper(grid,row+1,col1+1,col2+1,dp));
        
        int cur=(col1==col2)?grid[row][col1]:grid[row][col1]+grid[row][col2];
        dp[row][col1][col2]=cur+cur_max;
        return cur+cur_max;
        
        
            
    }
}
```

- Second
```java
class Solution {

    public int cherryPickup(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int dp[][][] = new int[m][n][n];

        for (int row = m - 1; row >= 0; row--) {
            for (int col1 = 0; col1 < n; col1++) {
                for (int col2 = 0; col2 < n; col2++) {
                    int result = 0;
                    // current cell
                    result += grid[row][col1];
                    if (col1 != col2) {
                        result += grid[row][col2];
                    }
                    // transition
                    if (row != m - 1) {
                        int max = 0;
                        for (int newCol1 = col1 - 1; newCol1 <= col1 + 1; newCol1++) {
                            for (int newCol2 = col2 - 1; newCol2 <= col2 + 1; newCol2++) {
                                if (newCol1 >= 0 && newCol1 < n && newCol2 >= 0 && newCol2 < n) {
                                    max = Math.max(max, dp[row + 1][newCol1][newCol2]);
                                }
                            }
                        }
                        result += max;
                    }
                    dp[row][col1][col2] = result;
                }
            }
        }
        return dp[0][0][n - 1];
    }
}
```
