(Leetcode Problem) 

Given a m x n matrix mat and an integer k, return a matrix answer where each answer[i][j] is the sum of all elements mat[r][c] for:

i - k <= r <= i + k,
j - k <= c <= j + k, and
(r, c) is a valid position in the matrix.
 

Example 1:

Input: mat = [[1,2,3],[4,5,6],[7,8,9]], k = 1
Output: [[12,21,16],[27,45,33],[24,39,28]]


CODE (JAVA) :

```
class Solution {
    public int[][] matrixBlockSum(int[][] mat, int k) {
     
        int[][] res = new int[mat.length][mat[0].length];
        
        for (int i = 0; i < mat.length; i++)
            for (int j = 0; j < mat[0].length; j++)
                res[i][j]=sumMat(k,mat,i,j);

        return res;
    }

    int sumMat(int k, int[][] mat, int i, int j) {
        int sum = 0;

        for (int a = i - k; a <= i + k; a++)
            if (a >= 0 && mat.length > a)
                for (int b = j - k; b <= j + k; b++)
                    if (b >= 0 && mat[0].length > b)
                        sum+=mat[a][b];

        return sum;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-22 223500](https://user-images.githubusercontent.com/73281015/213929399-dbd19353-cb0a-4cca-a365-0e6291cc0e29.png)

