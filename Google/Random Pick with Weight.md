(Leetcode Problem) 


You are given a 0-indexed array of positive integers w where w[i] describes the weight of the ith index.

You need to implement the function pickIndex(), which randomly picks an index in the range [0, w.length - 1] (inclusive) and returns it. The probability of picking an index i is w[i] / sum(w).

For example, if w = [1, 3], the probability of picking index 0 is 1 / (1 + 3) = 0.25 (i.e., 25%), and the probability of picking index 1 is 3 / (1 + 3) = 0.75 (i.e., 75%).
 

Example 1:

Input
["Solution","pickIndex"]
[[[1]],[]]
Output
[null,0]

Explanation
Solution solution = new Solution([1]);
solution.pickIndex(); // return 0. The only option is to return 0 since there is only one element in w.


CODE (JAVA) :

```
class Solution {
    int s[];
    Random r=new Random(); int mx=0;
    public Solution(int[] w) {
        s=new int[w.length];
        s[0]=w[0];
        for(int i=1;i<w.length;i++){
            s[i]=s[i-1]+w[i];
        }
        mx=s[s.length-1];
    }
    
    public int pickIndex() {
        int l=0;int h=s.length-1;
        int t=r.nextInt(mx)+1;
        while(l<=h){
            int m=l+(h-l)/2;
            if(s[m]==t) return m;
            else if(s[m]>t) h=m-1;
            else l=m+1;
        }
          return l;
    }
}



```
LEETCODE ACCEPTED :

![Screenshot 2023-01-22 235022](https://user-images.githubusercontent.com/73281015/213932964-ab2996bf-a032-4814-a0fc-c82070c1f409.png)
