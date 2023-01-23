(Leetcode Problem) 


A valid IP address consists of exactly four integers separated by single dots. Each integer is between 0 and 255 (inclusive) and cannot have leading zeros.

For example, "0.1.2.201" and "192.168.1.1" are valid IP addresses, but "0.011.255.245", "192.168.1.312" and "192.168@1.1" are invalid IP addresses.
Given a string s containing only digits, return all possible valid IP addresses that can be formed by inserting dots into s. You are not allowed to reorder or remove any digits in s. You may return the valid IP addresses in any order.

 

Example 1:

Input: s = "25525511135"
Output: ["255.255.11.135","255.255.111.35"]


CODE (JAVA) :

```
class Solution {
  

    //  List<String> list = new ArrayList<>();
    public List<String> restoreIpAddresses(String s) {
    //     recursion(s, "", 0, 4);
    //     System.out.println(list);
    //     return list;
    // }
    // void recursion(String s, String str, int i, int k){
    //     if(i == s.length() && k == 0){
    //         list.add(str.substring(0,str.length()-1));
    //         return;
    //     }
         
    //     for(int x = i; x < Math.min(s.length(),i+3); x++){
    //         if(k < 0) break;
    //         String sb = s.substring(i,x+1);
    //         int num = Integer.parseInt(sb);
    //         int size = sb.length();
    //         if(size == 2 && num < 10) continue;
    //         if(size == 3 && num < 100) continue;
    //         if(size == 3 && num > 255) continue;
    //         recursion(s, str + sb + ".", x+1, k-1);
    //     }
    // }







   List<String> ret = new ArrayList<>();
		
		StringBuffer ip = new StringBuffer();
		for(int a = 1 ; a < 4 ; ++ a)
		for(int b = 1 ; b < 4 ; ++ b)
	        for(int c = 1 ; c < 4 ; ++ c)
		for(int d = 1 ; d < 4 ; ++ d)
		{
			if(a + b + c + d == s.length() )
			{
				int n1 = Integer.parseInt(s.substring(0, a));
				int n2 = Integer.parseInt(s.substring(a, a+b));
				int n3 = Integer.parseInt(s.substring(a+b, a+b+c));
				int n4 = Integer.parseInt(s.substring(a+b+c));
				if(n1 <= 255 && n2 <= 255 && n3 <= 255 && n4 <= 255)
				{
					ip.append(n1).append('.').append(n2)
						.append('.').append(n3).append('.').append(n4);
					if(ip.length() == s.length() + 3) ret.add(ip.toString());
					ip.delete(0, ip.length());
				}
			}
		}
		return ret;
}
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-23 201949](https://user-images.githubusercontent.com/73281015/214069616-b2a6a693-cbf1-48ed-95df-9d730f6138b6.png)
