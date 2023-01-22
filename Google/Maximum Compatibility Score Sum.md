

(Leetcode Problem) 
There is a survey that consists of n questions where each question's answer is either 0 (no) or 1 (yes).

The survey was given to m students numbered from 0 to m - 1 and m mentors numbered from 0 to m - 1. The answers of the students are represented by a 2D integer array students where students[i] is an integer array that contains the answers of the ith student (0-indexed). The answers of the mentors are represented by a 2D integer array mentors where mentors[j] is an integer array that contains the answers of the jth mentor (0-indexed).

Each student will be assigned to one mentor, and each mentor will have one student assigned to them. The compatibility score of a student-mentor pair is the number of answers that are the same for both the student and the mentor.

For example, if the student's answers were [1, 0, 1] and the mentor's answers were [0, 0, 1], then their compatibility score is 2 because only the second and the third answers are the same.
You are tasked with finding the optimal student-mentor pairings to maximize the sum of the compatibility scores.

Given students and mentors, return the maximum compatibility score sum that can be achieved.

 

Example 1:

Input: students = [[1,1,0],[1,0,1],[0,0,1]], mentors = [[1,0,0],[0,0,1],[1,1,0]]
Output: 8
Explanation: We assign students to mentors in the following way:
- student 0 to mentor 2 with a compatibility score of 3.
- student 1 to mentor 0 with a compatibility score of 2.
- student 2 to mentor 1 with a compatibility score of 3.
The compatibility score sum is 3 + 2 + 3 = 8.



CODE (JAVA) :

```
class Solution {
    public int maxCompatibilitySum(int[][] students, int[][] mentors) {
        return recur(students, mentors, 0, 0, new Integer[students.length][256]);
    }

    private int recur(int[][] stu, int[][] men, int idx, int status, Integer[][] dp) {
        if (idx == stu.length) {
            return 0;
        }
        if (dp[idx][status] != null) {
            return dp[idx][status];
        }

        int res = 0;
        for (int i = 0; i < men.length; i++) {
            if ((status & (1 << i)) == 0) {
                res = Math.max(res, comp(stu[idx], men[i]) + recur(stu, men, idx + 1, status | (1 << i), dp));
            }
        }
        dp[idx][status] = res;
        return res;
    }

    private int comp(int[] stu, int[] men) {
        int res = 0;
        for (int i = 0; i < stu.length; i++) {
            if (stu[i] == men[i]) {
                res++;
            }
        }
        return res;
    }
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-22 111532](https://user-images.githubusercontent.com/73281015/213902482-275da96c-cdf0-464d-83b3-a4c3bc2e163e.png)
