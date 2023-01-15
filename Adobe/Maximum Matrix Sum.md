(Leetcode Problem) 
You are given an n x n integer matrix. You can do the following operation any number of times:

Choose any two adjacent elements of matrix and multiply each of them by -1.
Two elements are considered adjacent if and only if they share a border.

Your goal is to maximize the summation of the matrix's elements. Return the maximum sum of the matrix's elements using the operation mentioned above.

 

Example 1:


Input: matrix = [[1,-1],[-1,1]]
Output: 4
Explanation: We can follow the following steps to reach sum equals 4:
- Multiply the 2 elements in the first row by -1.
- Multiply the 2 elements in the first column by -1.



CODE (JAVA) :

```
class Solution {
    public long maxMatrixSum(int[][] matrix) {
         int numNegatives = 0;
        long totalSum=0;
        int minNeg = Integer.MIN_VALUE;
        int minPos = Integer.MAX_VALUE;        
        for (int i=0; i<matrix.length; i++) {
            for (int e=0; e<matrix[0].length; e++) {
                int value = matrix[i][e];
                if (value<0) {
                    numNegatives++;
                    totalSum = totalSum - value;
                    minNeg = value > minNeg ? value : minNeg;
                } else {
                    totalSum = totalSum + value;
                    minPos = value < minPos ? value : minPos;
                }
            }
        }        
        
        int min= Math.min(minPos, -minNeg);
        
        return totalSum - numNegatives%2*(min+min);
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-15 085943](https://user-images.githubusercontent.com/73281015/212521580-b91f3fe2-8bcc-4eb4-bb88-35abd908c061.png)
