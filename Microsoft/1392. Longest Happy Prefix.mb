(Leetcode Problem)
A string is called a happy prefix if is a non-empty prefix which is also a suffix (excluding itself).

Given a string s, return the longest happy prefix of s. Return an empty string "" if no such prefix exists.

 

Example 1:

Input: s = "level"
Output: "l"
Explanation: s contains 4 prefix excluding itself ("l", "le", "lev", "leve"), and suffix ("l", "el", "vel", "evel"). The largest prefix which is also suffix is given by "l".

CODE (JAVA) :

```
class Solution {
    public String longestPrefix(String s) {
        int a[] =new int[s.length()];
        char []c=s.toCharArray();
        int j=0 , i=1;
        while(i<c.length){
            if(c[j]==c[i]) {
                a[i]=j+1; i++ ; j++;
            }
            else{
                if(j!=0) j=a[j-1];
                else i++;
            }
        }
        return s.substring(0,a[a.length-1]);
    }
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-03 ](https://user-images.githubusercontent.com/73281015/210769437-6b0d62df-557c-43fb-8e48-39307301eb7f.png)
