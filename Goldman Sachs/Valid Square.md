(Leetcode Problem)
Given the coordinates of four points in 2D space p1, p2, p3 and p4, return true if the four points construct a square.

The coordinate of a point pi is represented as [xi, yi]. The input is not given in any order.

A valid square has four equal sides with positive length and four equal angles (90-degree angles).

 

Example 1:

Input: p1 = [0,0], p2 = [1,1], p3 = [1,0], p4 = [0,1]
Output: true

CODE (JAVA) :

 class Solution {
    public static boolean validSquare(int[] p1, int[] p2, int[] p3, int[] p4) {
        return isSameLength(p1, p3, p2, p4) &&
                isSameLength(p1, p2, p3, p4) &&
                isSameLength(p1, p4, p2, p3) &&
                (isSameLength(p1, p2, p2, p3) || isSameLength(p1, p3, p2, p3) || isSameLength(p1, p2, p1, p3));
    }

    public static int distanceSquare(int[] p1, int[] p2){
        int xSquare = (p1[0] - p2[0]) * (p1[0] - p2[0]);
        int ySquare = (p1[1] - p2[1]) * (p1[1] - p2[1]);
        return xSquare + ySquare;
    }

    public static boolean isSameLength(int[] p1, int[] p2, int[] p3, int[] p4){
        return distanceSquare(p1, p2) == distanceSquare(p3, p4) && distanceSquare(p1, p2) != 0;
    }
}
LEETCODE ACCEPTED :

![Screenshot 2023-01-09 101259](https://user-images.githubusercontent.com/73281015/211242397-4573a471-da25-4061-a096-2cdcb0b315b0.png)
