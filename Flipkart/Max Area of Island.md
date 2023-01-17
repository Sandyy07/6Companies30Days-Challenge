(Leetcode Problem) 

You are given an m x n binary matrix grid. An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The area of an island is the number of cells with a value 1 in the island.

Return the maximum area of an island in grid. If there is no island, return 0.

 

Example 1:


Input: grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
Output: 6
Explanation: The answer is not 11, because the island must be connected 4-directionally.


CODE (JAVA) :

```
class Solution {

    int sum = 0;
    public int maxAreaOfIsland(int[][] grid) {
        int max = 0;
       for(int i = 0; i<grid.length;i++){
            for(int j = 0; j<grid[i].length;j++){
                if(grid[i][j]==1){
                    sum = 0; 
                    h(grid,i,j);
                    max  = Math.max(max,sum);
                }
            }
        }
        return max;
 }
    public void h(int[][] grid ,int i ,int j){
        if(i>=grid.length || j>=grid[0].length || i<0|| j<0 || grid[i][j]==0){
            return ;
        }
        sum++;
        grid[i][j] = 0;
        h(grid,i,j+1);
        h(grid,i,j-1);
        h(grid,i+1,j);
        h(grid,i-1,j);
    }
}



```
LEETCODE ACCEPTED :

![Screenshot 2023-01-17 143651](https://user-images.githubusercontent.com/73281015/212855556-fa1e50d9-3575-4406-9972-0b73c9fecb04.png)
