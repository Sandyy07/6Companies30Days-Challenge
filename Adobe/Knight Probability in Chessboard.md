
(Leetcode Problem) 


On an n x n chessboard, a knight starts at the cell (row, column) and attempts to make exactly k moves. The rows and columns are 0-indexed, so the top-left cell is (0, 0), and the bottom-right cell is (n - 1, n - 1).

A chess knight has eight possible moves it can make, as illustrated below. Each move is two cells in a cardinal direction, then one cell in an orthogonal direction.


Each time the knight is to move, it chooses one of eight possible moves uniformly at random (even if the piece would go off the chessboard) and moves there.

The knight continues moving until it has made exactly k moves or has moved off the chessboard.

Return the probability that the knight remains on the board after it has stopped moving.

 

Example 1:

Input: n = 3, k = 2, row = 0, column = 0
Output: 0.06250
Explanation: There are two moves (to (1,2), (2,1)) that will keep the knight on the board.
From each of those positions, there are also two moves that will keep the knight on the board.
The total probability the knight stays on the board is 0.0625.

CODE (JAVA) :

```
class Solution {
    int[][] moves=new int[][]{{-2,-1},{-2,1},{-1,-2},{-1,2},{1,-2},{1,2},{2,-1},{2,1}};

    public double knightProbability(int N, int K, int r, int c) {
        int center=(N+1)/2;

        double[][][] board=new double[K+1][center][center];
        double available=find(board,r,c,N,K,center);
        return available/Math.pow(8,K);
    }

    private int transform(int n,int center,int x){
        return x<center?x:n-1-x;
    }
    private double find(double[][][] board,int i,int j,int n, int k, int center) {
        if(i<0||j<0||i>=n||j>=n)
            return 0;
        if(k==0)
            return 1;
        i=transform(n,center,i);
        j=transform(n,center,j);
        if(board[k][i][j]!=0) return board[k][i][j];
        double res=0;
        for(int[] move:moves){
            res+=find(board,i+move[0],j+move[1],n,k-1,center);
        }
        board[k][i][j]=res;
        return res;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-14 174956](https://user-images.githubusercontent.com/73281015/212471331-82326326-e8b4-44ae-ac72-2299ebc57e90.png)
