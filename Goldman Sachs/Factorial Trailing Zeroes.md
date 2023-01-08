(Leetcode Problem)

Given an integer n, return the number of trailing zeroes in n!.

Note that n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1.

 

Example 1:

Input: n = 3
Output: 0
Explanation: 3! = 6, no trailing zero.

CODE (JAVA) :

```
class Solution {
    public int trailingZeroes(int n) {
        int ans=0;
        while(n>0){
            n/=5;
            ans+=n;
        }
        return ans;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-09 005703](https://user-images.githubusercontent.com/73281015/211214966-3ffde8e9-26bd-4dea-b26e-7869a220bfac.png)

