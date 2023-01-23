(Leetcode Problem) 

Given a 2D grid consists of 0s (land) and 1s (water).  An island is a maximal 4-directionally connected group of 0s and a closed island is an island totally (all left, top, right, bottom) surrounded by 1s.

Return the number of closed islands.

 

Example 1:



Input: grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
Output: 2
Explanation: 
Islands in gray are closed because they are completely surrounded by water (group of 1s).


CODE (JAVA) :

```

class Solution {
    public int closedIsland(int[][] grid) {
        int c=0;
        int n=grid.length;
        int m=grid[0].length;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(i*j==0 || i==n-1 || j==m-1){
                   if(grid[i][j]==0) dfs(i,j,n,m,grid);
                }
            }
        }

              for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
             
                   if(grid[i][j]==0) {
                          c++;
                          dfs(i,j,n,m,grid);
                   }
            }
        }

    return c;
  
    }
          void dfs(int i, int j , int n, int m, int [][]grid){
              grid[i][j]=1;
            int a[]={1,-1,0,0};
            int b[]={0,0,1,-1};
            for(int k=0;k<4;k++){
                int c=i+a[k]; int d=j+b[k];
                if(c>=0 && c<n && d>=0 && d<m && grid[c][d]==0) 
                dfs(c,d,n,m,grid);
            }

        }
}

```
LEETCODE ACCEPTED :


![Screenshot 2023-01-23 194015](https://user-images.githubusercontent.com/73281015/214060446-04ef831c-eef2-40b2-a69d-bb0ee5c4cd69.png)

