(Leetcode Problem) 

The demons had captured the princess and imprisoned her in the bottom-right corner of a dungeon. The dungeon consists of m x n rooms laid out in a 2D grid. Our valiant knight was initially positioned in the top-left room and must fight his way through dungeon to rescue the princess.

The knight has an initial health point represented by a positive integer. If at any point his health point drops to 0 or below, he dies immediately.

Some of the rooms are guarded by demons (represented by negative integers), so the knight loses health upon entering these rooms; other rooms are either empty (represented as 0) or contain magic orbs that increase the knight's health (represented by positive integers).

To reach the princess as quickly as possible, the knight decides to move only rightward or downward in each step.

Return the knight's minimum initial health so that he can rescue the princess.

Note that any room can contain threats or power-ups, even the first room the knight enters and the bottom-right room where the princess is imprisoned.

 

Example 1:


Input: dungeon = [[-2,-3,3],[-5,-10,1],[10,30,-5]]
Output: 7
Explanation: The initial health of the knight must be at least 7 if he follows the optimal path: RIGHT-> RIGHT -> DOWN -> DOWN.


CODE (JAVA) :

```
class Solution {
    public int calculateMinimumHP(int[][] dungeon) {
      if (dungeon == null || dungeon.length == 0 || dungeon[0].length == 0)
            return 0;

        int m = dungeon.length;
        int n = dungeon[0].length;
        int dp[] = new int[n];

        for (int i = m - 1; i >= 0; i--) {

            for (int j = n - 1; j >= 0; j--) {

                if (i == m - 1 && j == n - 1)
                    dp[j] = dungeon[i][j] > 0 ? 1 : -dungeon[i][j] + 1;
                else if (i == m - 1)
                    dp[j] = dp[j + 1] - dungeon[i][j];
                else if (j == n - 1)
                    dp[j] = dp[j] - dungeon[i][j];
                else {

                    dp[j] = Math.min(dp[j], dp[j + 1]) - dungeon[i][j];
                }

                dp[j] = dp[j] <= 0 ? 1 : dp[j];

            }
        }

        return dp[0];   
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-15 181239](https://user-images.githubusercontent.com/73281015/212541284-f3f15d5b-081c-4d35-9ab8-303bdd996f9d.png)
