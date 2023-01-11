(Leetcode Problem)

Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.

If multiple answers are possible, return any of them.

It is guaranteed that the length of the answer string is less than 104 for all the given inputs.

 

Example 1:

Input: numerator = 1, denominator = 2
Output: "0.5"



CODE (JAVA) :

```
class Solution {
    public String fractionToDecimal(int n, int d) 
    {
        long a = Math.abs((long)n);
        long b = Math.abs((long)d);
        
        StringBuilder sb = new StringBuilder();
        
        if( (n<0 && d>0) || (n>0 && d<0))
            sb.append('-');
        
        sb.append(a/b);
        a = a%b;
        
        if(a > 0)
            sb.append('.');
        
        HashMap<Long,Integer> map = new HashMap<>();
        
        while(!map.containsKey(a))
        {
            map.put(a , map.size());
            a = a*10;
            
            if(a > 0)
                sb.append(a/b);
            
            a = a%b;
        }
        
        if(a > 0)
        {
            sb.insert(sb.length()-(map.size()-map.get(a)) , '(');
            sb.append(')');
        }
        
        return sb.toString();
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-11 192857](https://user-images.githubusercontent.com/73281015/211824938-850f6ca3-9f99-4e57-b76c-4150e012c5fc.png)
