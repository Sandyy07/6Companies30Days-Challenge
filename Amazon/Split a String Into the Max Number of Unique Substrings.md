(Leetcode Problem) 

Given a string s, return the maximum number of unique substrings that the given string can be split into.

You can split string s into any list of non-empty substrings, where the concatenation of the substrings forms the original string. However, you must split the substrings such that all of them are unique.

A substring is a contiguous sequence of characters within a string.

 

Example 1:

Input: s = "ababccc"
Output: 5
Explanation: One way to split maximally is ['a', 'b', 'ab', 'c', 'cc']. Splitting like ['a', 'b', 'a', 'b', 'c', 'cc'] is not valid as you have 'a' and 'b' multiple times.


CODE (JAVA) :

```
class Solution {
    public int maxUniqueSplit(String s) {
        HashSet<String> hs=new HashSet<>();
        return g(0,s,hs,"");
    }


    int g(int i, String s, HashSet<String> hs , String t){
        if(i==s.length()) return 0;
        else{
            t+=s.charAt(i); 
            int a1=Integer.MIN_VALUE/2;
            int a2=Integer.MIN_VALUE/2;
            if(!hs.contains(t)){
                hs.add(t);
                a1=1+g(i+1,s,hs,"");
                hs.remove(t);
            }
            a2=g(i+1,s,hs,t);
            return Math.max(a1,a2);
        }
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 000610](https://user-images.githubusercontent.com/73281015/215348318-7ba44d3c-3fd6-488a-b343-04b53c83c73b.png)


