(Leetcode Problem) 

You are given an m x n integer matrix grid.

We define an hourglass as a part of the matrix with the following form:


Return the maximum sum of the elements of an hourglass.

Note that an hourglass cannot be rotated and must be entirely contained within the matrix.

 

Example 1:


Input: grid = [[6,2,1,3],[4,2,1,5],[9,2,8,7],[4,1,2,9]]
Output: 30
Explanation: The cells shown above represent the hourglass with the maximum sum: 6 + 2 + 1 + 2 + 9 + 2 + 8 = 30.


CODE (JAVA) :

```
class Solution {
    public int maxSum(int[][] grid) {
        int n=grid.length; int m=grid[0].length; int ma=0;
        for(int i=1;i+1<n;i++){
            for(int j=1;j+1<m;j++){
                int s=grid[i][j]+grid[i-1][j]+grid[i+1][j]+grid[i-1][j-1]+grid[i+1][j+1]+grid[i-1][j+1]+grid[i+1][j-1];
                 ma=Math.max(ma,s);
            }
        }
        return ma;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-30 100807](https://user-images.githubusercontent.com/73281015/215388681-a97805e7-389a-4dab-be80-c0f52f0dea1d.png)

