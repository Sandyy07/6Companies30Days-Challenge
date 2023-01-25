(Leetcode Problem) 
You are given an n x n integer matrix grid where each value grid[i][j] represents the elevation at that point (i, j).

The rain starts to fall. At time t, the depth of the water everywhere is t. You can swim from a square to another 4-directionally adjacent square if and only if the elevation of both squares individually are at most t. You can swim infinite distances in zero time. Of course, you must stay within the boundaries of the grid during your swim.

Return the least time until you can reach the bottom right square (n - 1, n - 1) if you start at the top left square (0, 0).

 

Example 1:


Input: grid = [[0,2],[1,3]]
Output: 3
Explanation:
At time 0, you are in grid location (0, 0).
You cannot go anywhere else because 4-directionally adjacent neighbors have a higher elevation than t = 0.
You cannot reach point (1, 1) until time 3.
When the depth of water is 3, we can swim anywhere inside the grid.



CODE (JAVA) :

```
class Solution {
        public static final int[] X = {1, 0, -1, 0};
    public static final int[] Y = {0, 1, 0, -1};
    public int swimInWater(int[][] grid) {
        int n=grid.length; int mi=grid[0].length;
        int l=0, h=n*n-1;
        while(l<h){
            int m=l+(h-l)/2;
            int [][] v=new int[n][n];
            if(dfs(m,0,0,grid,v,n)) h=m;
            else l=m+1;
        }
        return l;
    }


    boolean dfs(int m, int i, int j ,int [][] grid,int [][] v,int n){
        if(i==n-1 && j==n-1) return true;
        v[i][j]=1;
        for(int p=0;p<X.length;p++){
            int ni=i+X[p];
            int nj=j+Y[p];
            if(ni>=0 && nj>=0 && ni<n && nj<n && v[ni][nj]==0 && grid[i][j]<=m && grid[ni][nj]<=m){
                if(dfs(m,ni,nj,grid,v,n)) return true;
            }
        }
        return false;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-25 230346](https://user-images.githubusercontent.com/73281015/214638917-1f1b211e-5a25-4020-89ab-ba4df80ab577.png)

