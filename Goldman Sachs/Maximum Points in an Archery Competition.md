(Leetcode Problem) You are given two 0-indexed arrays nums1 and nums2 of length n, both of which are permutations of [0, 1, ..., n - 1].

Alice and Bob are opponents in an archery competition. The competition has set the following rules:

Alice first shoots numArrows arrows and then Bob shoots numArrows arrows.
The points are then calculated as follows:
The target has integer scoring sections ranging from 0 to 11 inclusive.
For each section of the target with score k (in between 0 to 11), say Alice and Bob have shot ak and bk arrows on that section respectively. If ak >= bk, then Alice takes k points. If ak < bk, then Bob takes k points.
However, if ak == bk == 0, then nobody takes k points.
For example, if Alice and Bob both shot 2 arrows on the section with score 11, then Alice takes 11 points. On the other hand, if Alice shot 0 arrows on the section with score 11 and Bob shot 2 arrows on that same section, then Bob takes 11 points.

You are given the integer numArrows and an integer array aliceArrows of size 12, which represents the number of arrows Alice shot on each scoring section from 0 to 11. Now, Bob wants to maximize the total number of points he can obtain.

Return the array bobArrows which represents the number of arrows Bob shot on each scoring section from 0 to 11. The sum of the values in bobArrows should equal numArrows.

If there are multiple ways for Bob to earn the maximum total points, return any one of them.

 

Example 1:


Input: numArrows = 9, aliceArrows = [1,1,0,1,0,0,2,1,0,1,2,0]
Output: [0,0,0,0,1,1,0,0,1,2,3,1]
Explanation: The table above shows how the competition is scored. 
Bob earns a total point of 4 + 5 + 8 + 9 + 10 + 11 = 47.
It can be shown that Bob cannot obtain a score higher than 47 points.

CODE (JAVA) :

```
class Solution {
    int[] res = new int[12];
    int max = 0;
    public int[] maximumBobPoints(int numArrows, int[] aliceArrows) {
        compute(numArrows, aliceArrows, new int[12], 11, 0);
        return res;
    }

    private void compute(int numArrows, int[] aliceArrows, int[] bobArrows, int idx, int point) {
        if (idx == 0) {
            if (point > max) {
                max = point;
                bobArrows[idx] = numArrows;
                res = bobArrows.clone();
            }
            return;
        }
        compute(numArrows, aliceArrows, bobArrows, idx - 1, point);
        if (numArrows > aliceArrows[idx]) {
            bobArrows[idx] = aliceArrows[idx] + 1;
            compute(numArrows - bobArrows[idx], aliceArrows, bobArrows, idx - 1, point + idx);
            bobArrows[idx] = 0;
        }
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-10 124711](https://user-images.githubusercontent.com/73281015/211486257-d88e0992-8b3a-483b-be46-0dd18ac45e8c.png)

