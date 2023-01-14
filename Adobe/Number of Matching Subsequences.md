(Leetcode Problem) 
Given a string s and an array of strings words, return the number of words[i] that is a subsequence of s.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
 

Example 1:

Input: s = "abcde", words = ["a","bb","acd","ace"]
Output: 3
Explanation: There are three strings in words that are a subsequence of s: "a", "acd", "ace".



CODE (JAVA) :

```
class Solution {
    public int numMatchingSubseq(String s, String[] words) {
        
        Map<String,Integer> map = new HashMap<>();
        for(String str:words){
            map.put(str,map.getOrDefault(str,0)+1);
        }
        
        int ans = 0;
        char ch[] = s.toCharArray();
        
        for(String str:map.keySet()){
            
            char t[] = str.toCharArray();
            int i = 0;
            int j = 0;
            
            while(i<ch.length && j<t.length){
                if(ch[i]==t[j]){
                    i++;
                    j++;
                }else{
                    i++;
                }
            }
            
            if(j==t.length){
                ans+=map.get(str);
            }
            
        }
        
      return ans;  
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-14 192213](https://user-images.githubusercontent.com/73281015/212475344-0eb67092-1f7a-4871-b6f9-227589ef84bd.png)
