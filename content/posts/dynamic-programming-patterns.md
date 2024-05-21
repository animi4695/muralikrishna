---
title: "Dynamic Programming Notes"
date: 2024-05-13T14:11:06+05:30
draft: true
toc: false
images:
tags: [programming, problemsolving, dsa, interview]
---  

#### Introduction
Dynamic Programming is one of the hardest topics in interviews atleast for me. I'm trying to make notes of various patterns I come across the web. The following is like a cheatsheet for myself to go through while preparing for interview.

Long story short, DP is breaking a problem into subproblems and see if the problems were already solved before. If so, store while calculating it the first time and use it when the same subproblem occurs again to avoid re-computation.

#### Identifying & Solving DP problem
know its properties 
 - Overlapping subproblems
 - Optimal substructure (max/min, shortest/longest etc)

Can be solved with 2 approaches.
1) Top Down with Memoization
2) Bottom up with Tabulation

For me Top down approach really clicked compared to the bottom up.

#### Patterns

- **Minimum (Maximum) path to reach a target**
  - **General statement** - Given target, find max/min cost/path/sum to reach target.
  -  **Approach** - For eg, to reach a target i (a subproblem), min/max cost/path/sum to reach target_i = min/max of cost/path/sum to reach target_i-1 + cost/path/sum of current path. Again, to reach min/max of cost/path/sum to reach target_i-1 = min/max of cost/path/sum to reach target_i-2 + cost/path/sum of current path
        ```
        ways[i] = min/max (ways[i-1] + ways[i-2] +... + ways[i-k]) + cost/path[i]
        ```
       - **Top Down**
        ```
        // base cases ...
        
        // ans already calculated return ...
        
        // not found calculate ...
        for (int i = 0; i < ways.size(); ++i) {
            result = min(result, topDown(target - ways[i]) + cost/path/sum);
        }

        // store for future
        return memo[/*state parameters*/] = result;
        ```
        - **Bottom Up**
        ```
        // base cases ...

        for (int i = 1; i <= target; ++i) {
            for (int j = 0; j < ways.size(); ++j) {
                if (ways[j] <= i) {
                    dp[i] = min(dp[i], dp[i - ways[j]] + cost / path / sum) ;
                }
            }
        }
        return dp[target]
        ``` 
    - **Example 1**
        - **Coin change** - You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money. Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1
        - The above question can be turned into general statement - Given target (*integer amount representing a total amount of money*), find max/min (*Return the fewest number of coins*) to reach target.
        
    - **Top Down**
        ```
        // coin change example
        for (int i = 0; i < coins.size(); ++i) {
            if (coins[i] <= target) { // check validity of a sub-problem
                result = min(res, CoinChange(target - coins[i], coins) + 1);
            }
        }
        return memo[target] = result;
        ```
    - **Bottom Up**
        ```
        // coin change example
        for (int i = 1; i <= amount; ++i) {
            for (int j = 0; j < coins.size(); ++j) {
                if (coins[j] <= i) {
                    dp[i] = min(dp[i], dp[i - coins[j]] + 1);
                }
            }
        }
        return dp[amount]
        ```

    - **Example 2**
        - **Minimum Path Sum** - Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path
        Note: You can only move either down or right at any point in time.
        - The above question can be turned into general statement - Given target (*path to bottom right*), find max/min (*return min path cost*) to reach target.
        
    - **Top Down**
        ```
        // we need to explore 2 available directions
        for (int direction = 0; direction < 2; ++direction) {
            int new_i = i + (direction == 0 ? 1 : 0);
            int new_j = j + (direction == 1 ? 1 : 0);
            if (new_i < grid.size() && new_j < grid[0].size()) { // check validity of a sub-problem
                result = min(result, pathSum(new_i, new_j, grid, memo) + grid[i][j]);
            }
        }
        return memo[i][j] = result;

        *or more natural way*

        int result = min(pathSum(grid[i][j+1], grid, memo), pathSum(grid[i+1][j], grid, memo)) + grid[i][j];
        return memo[i][j] = result;
        ```
    - **Bottom Up**
        ```
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                grid[i][j] = min(grid[i-1][j], grid[i][j-1]) + grid[i][j];
            }
        }
        return grid[n-1][m-1]
        ```
---
*References :*   
