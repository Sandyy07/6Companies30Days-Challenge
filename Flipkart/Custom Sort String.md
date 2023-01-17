(Leetcode Problem) 
You are given two strings order and s. All the characters of order are unique and were sorted in some custom order previously.

Permute the characters of s so that they match the order that order was sorted. More specifically, if a character x occurs before a character y in order, then x should occur before y in the permuted string.

Return any permutation of s that satisfies this property.

 

Example 1:

Input: order = "cba", s = "abcd"
Output: "cbad"
Explanation: 
"a", "b", "c" appear in order, so the order of "a", "b", "c" should be "c", "b", and "a". 
Since "d" does not appear in order, it can be at any position in the returned string. "dcba", "cdba", "cbda" are also valid outputs.



CODE (JAVA) :

```
class Solution {
    public String customSortString(String order, String s) {



        String s1=""; String s2="";
        int f[]=new int[26];
        for(var x:order.toCharArray()) f[x-'a']++;
        for(var x:s.toCharArray()) {
            if(f[x-'a']==0) s2+=x;
            else f[x-'a']++;
        }
        for(var x:order.toCharArray()){
            while(f[x-'a']>1) {
                s1+=x; f[x-'a']--;
            }
        }
        return s1+s2;

    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-17 145647](https://user-images.githubusercontent.com/73281015/212860185-d2838577-26e7-4b31-a633-9d312690d17c.png)

