(Leetcode Problem) 

Return the number of distinct non-empty substrings of text that can be written as the concatenation of some string with itself (i.e. it can be written as a + a where a is some string).

 

Example 1:

Input: text = "abcabcabc"
Output: 3
Explanation: The 3 substrings are "abcabc", "bcabca" and "cabcab".



CODE (JAVA) :

```
// class Solution {
//     public int distinctEchoSubstrings(String text) {
//         int n=text.length();
//         HashSet<String> h=new HashSet<>();
//         for(int x=1;x<=n/2;x++){
//             int c=0;
//             for(int l=0,r=x;r<n;l++,r++){
//                 if(text.charAt(l)==text.charAt(r)) c++;
//                 else c=0;
//                 if(c==x){
//                     String b=text.substring(l,r+1);
//                     h.add(b);
//                     c--;
//                 }
//             }
//         }
//         return h.size();
//     }
// }

class Solution {
    long hash[];
    long pow[];
    long r=256;
    long mod=(long)Math.pow(10,9)+7;
    public void process(String s,int n)
    {
        hash=new long[n];
        pow=new long[n];
        pow[0]=1;
        for(int i=1;i<n;i++)
        {
            hash[i]=(hash[i-1]*r+s.charAt(i))%mod;
            pow[i]=(pow[i-1]*r)%mod;
        }
    }
    public long calc(int l,int r)
    {
        long hashValue=(hash[r]-hash[l]*pow[r-l]%mod+mod)%mod;
        return hashValue;
    }
    public int distinctEchoSubstrings(String text) {
        int n=text.length();
        process(text,n);
        HashSet<Long> hset=new HashSet<>();
        for(int len=1;len<=n/2;len++)
        {
            int c=0;
            for(int l=0,r=len;r<n;l++,r++)
            {
                if(text.charAt(l)==text.charAt(r))
                {
                   c++; 
                }
                else
                {
                    c=0;
                }
                if(c==len)
                {
                    long hv=calc(l,r);
                    hset.add(hv);
                    c--;
                }
            }
        }
        return hset.size();
        
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-25 222909](https://user-images.githubusercontent.com/73281015/214629305-ae2c8d4a-2af3-447f-aa75-7cd26a210de1.png)

