(Leetcode Problem)
n passengers board an airplane with exactly n seats. The first passenger has lost the ticket and picks a seat randomly. But after that, the rest of the passengers will:

Take their own seat if it is still available, and
Pick other seats randomly when they find their seat occupied
Return the probability that the nth person gets his own seat.

 

Example 1:

Input: n = 1
Output: 1.00000
Explanation: The first person can only get the first seat.

CODE (JAVA) :

class Solution {
    public double nthPersonGetsNthSeat(int n) {
          return n==1? 1 : .5;
    }
}

LEETCODE ACCEPTED :
![Screenshot 2023-01-05 ](https://user-images.githubusercontent.com/73281015/210773396-fed40bba-bb54-490b-b312-feedd11c09f5.png)
