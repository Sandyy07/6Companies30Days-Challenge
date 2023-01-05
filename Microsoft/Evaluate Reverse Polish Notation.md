(Leetcode Problem)

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

Example 1
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9

```
CODE (JAVA) :

class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>() ;
        Set<String> o = new HashSet<>(Arrays.asList("+", "-", "*", "/")) ;
        for (String i:tokens) 
        {
            if(!o.contains(i)) 
                stack.push(Integer.valueOf(i));
            else 
            {
                int a = stack.pop(), b = stack.pop();
                if(i.equals("+")) 
                    stack.push(a + b);
                else if(i.equals("-")) 
                    stack.push(b - a);
                else if(i.equals("*")) 
                    stack.push(a*b);
                else 
                    stack.push(b/a);
            }
        }
        return stack.peek() ;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-05 ](https://user-images.githubusercontent.com/73281015/210766827-24ad614f-e944-4d14-a05c-1eebe5ad1565.png)
