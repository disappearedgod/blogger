---
title: LeetCode|Greedy|200 Number of Islands
date: 2020-07-15 12:12:57
categories: 
- LeetCode
type: ["LeetCode","DFS"]

---

# Problem

Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

 

Example 1:

> Input: grid = [
>   ["1","1","1","1","0"],
>   ["1","1","0","1","0"],
>   ["1","1","0","0","0"],
>   ["0","0","0","0","0"]
> ]
> Output: 1

Example 2:

`Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3`


# Solve
[here](https://leetcode.com/problems/number-of-islands/discuss/429842/JavaScript-DFS-Commented-Thought-Process-Beats-100-Time-and-Space)

Below is what I typed out on a google doc in preparation for a google phone interview.
I thought it may be helpful for others to see and give feedback on my thought process, and if it makes sense/is followable. After all, that's what I want my interviewer to do, understand me.
Goal: Count number of islands
Rules:

An island is surrounded by water(0's)
We count things apart of our island if it is horizontal or vertical connected
Plan:
Start at the top left of the 2d array, and visit the first row, and all its columns, trying to find the start of the first island
Once we find a 1, we can increment the number of islands, but we want to know where the island ends. So let’s look and follow any of the horizontal or vertical spots near the current position we are on.
First, let’s mark the current start/visited parts of the islands as visited by turning them into a 0,
Second, explore all the adjacent possibilities,
If one of them is a 1, recursively turn it into a 0 and check its children
Once we are done, we should have gotten rid of the island that we discovered and can move on to the next island, if it exists in the 2d array

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
    if(!grid)
        return 0;
    let res = 0;
    let m =0;
    let n = 0;
    
    
    for(let i = 0; i < grid.length; i++){
        for(let j = 0; j < grid[i].length; j++){
            res += grid[i][j] -"0";
            dfs(i, j, grid);
        }
    }
    return res;
};

function dfs(x, y, array){
    if(x<0 || y< 0|| x>= array.length || y>= array[0].length || array[x][y] ==="0"){
        return;
}
    array[x][y] = "0";
    dfs(x-1, y, array);
    dfs(x+1, y, array);
    dfs(x, y-1, array);
    dfs(x, y+1, array);
}



```


