(Leetcode Problem) 
Given a binary string s and an integer k, return true if every binary code of length k is a substring of s. Otherwise, return false.

 

Example 1:

Input: s = "00110110", k = 2
Output: true
Explanation: The binary codes of length 2 are "00", "01", "10" and "11". They can be all found as substrings at indices 0, 1, 3 and 2 respectively.



CODE (JAVA) :

```
class Solution {
    public boolean hasAllCodes(String s, int k) {
    var set = new HashSet<String>();
	for (var i = 0; i + k <= s.length(); i++)
		set.add(s.substring(i, i + k));
	return set.size() == Math.pow(2, k);
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-17 140804](https://user-images.githubusercontent.com/73281015/212849542-ef2f2736-83ad-4b2b-884c-0092dd7cc1e9.png)
