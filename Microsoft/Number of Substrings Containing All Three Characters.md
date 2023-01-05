(Leetcode Problem)
Given a string s consisting only of characters a, b and c.

Return the number of substrings containing at least one occurrence of all these characters a, b and c.


Example 1:

Input: s = "abcabc"
Output: 10
Explanation: The substrings containing at least one occurrence of the characters a, b and c are "abc", "abca", "abcab", "abcabc", "bca", "bcab", "bcabc", "cab", "cabc" and "abc" (again). 

CODE (JAVA) :

 ```
 class Solution {
      public int numberOfSubstrings(String s) {
        int[] count = new int[3];
        int ans = 0;
        for (int lo = -1, hi = 0; hi < s.length(); ++hi) {
            ++count[s.charAt(hi) - 'a'];
            while (count[0] > 0 && count[1] > 0 && count[2] > 0) {
                ans += s.length() - hi;  
                --count[s.charAt(++lo) - 'a'];
            }
        } 
        return ans;        
    }
}
 ```
LEETCODE ACCEPTED :
![Screenshot 2023-01-03](https://user-images.githubusercontent.com/73281015/210772114-1a7763a5-632d-4085-9c90-7473a15e3501.png)
