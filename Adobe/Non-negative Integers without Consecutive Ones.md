(Leetcode Problem) 
Given a positive integer n, return the number of the integers in the range [0, n] whose binary representations do not contain consecutive ones.

 

Example 1:

Input: n = 5
Output: 5
Explanation:
Here are the non-negative integers <= 5 with their corresponding binary representations:
0 : 0
1 : 1
2 : 10
3 : 11
4 : 100
5 : 101
Among them, only integer 3 disobeys the rule (two consecutive ones) and the other 5 satisfy the rule. 



CODE (JAVA) :

```
class Solution {
    public int findIntegers(int n) {
        // int ze=1; int oe=1; 
        // int s=ze+oe;
        // if(n==1) return s;
        // int i=2;
        // while(i<n){
        //     oe=ze;
        //     ze=s;
        //     s=ze+oe;
        // }
        // return s;

         int S[] = new int[32];
        S[1] = 1;
		
        for (int i = 2; i <= 31; i++) {
            S[i] = S[i-1] + S[i-2];
        }
        
        for (int i = 1; i <= 31; i++) {
            S[i] += S[i-1];
        }
        
        int res = 0;
        for (int i = 31, prev = 0; i >= 0; i--) {
            if ((n & (1 << i)) != 0) {
                res += S[i];
                
                if (prev == i+1) {
                    break;
                }
                
                prev = i;
                res++;
            }
    }
    return res+1;
}
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-12 011701](https://user-images.githubusercontent.com/73281015/211903255-39656689-f97c-48bf-9fae-77e3dbe9f836.png)
