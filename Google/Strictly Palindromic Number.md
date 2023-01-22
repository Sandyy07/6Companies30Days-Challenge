
(Leetcode Problem) 

An integer n is strictly palindromic if, for every base b between 2 and n - 2 (inclusive), the string representation of the integer n in base b is palindromic.

Given an integer n, return true if n is strictly palindromic and false otherwise.

A string is palindromic if it reads the same forward and backward.

 

Example 1:

Input: n = 9
Output: false
Explanation: In base 2: 9 = 1001 (base 2), which is palindromic.
In base 3: 9 = 100 (base 3), which is not palindromic.
Therefore, 9 is not strictly palindromic so we return false.
Note that in bases 4, 5, 6, and 7, n = 9 is also not palindromic.


CODE (JAVA) :

```
class Solution {
    public boolean isStrictlyPalindromic(int n) {
        boolean f=true;
      for(int i=2;i<=n-2;i++){
          String s=bit(n,i);
          if(!isPal(s)){
              f=false; break ;
          }
      }  
          return f;
    }

    String bit(int n,int b){
        // String s="";
        // while(n!=0){
        //     if(n%b!=0){
        //         int m=n%b;
        //         s+=String.valueOf(m)+'0';
        //         n/=b;
        //     }
        //     else{
        //         s+='0';
        //         n/=b;
        //     }
        // }
        // return s;

        return Integer.toString(n,b);
    }

     boolean isPal(String s)
    {
        int n=s.length();
        if(n<=1)
         return true;
        
        int j=0;
        int k=n/2;
        
        for(int i=1;i<=k;i++)
        {        
            if(n%2==1)
            {
                if(s.charAt(k-i)!=s.charAt(k+i))
                    return false;
            }
            else
            {
                if(s.charAt(k-i)!=s.charAt(k+i-1))
                    return false;                
            }
        }
        
        return true;
    }


}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-22 114246](https://user-images.githubusercontent.com/73281015/213903213-615cf243-5bf9-451d-abe6-ea78ddb94168.png)

