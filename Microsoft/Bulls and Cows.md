(Leetcode Problem)

You are playing the Bulls and Cows game with your friend.
You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:
The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls. Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.
The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.

Example 1 : 
Input: secret = "1807", guess = "7810"
Output: "1A3B"
Explanation: Bulls are connected with a '|' and cows are underlined:
"1807"
  |
"7810"
  
  
  CODE (JAVA) : 
```
  class Solution {
    public String getHint(String secret, String guess) {
        int bulls=0, cows =0;
        int[] numbers = new int[10];
        for(int i=0; i<secret.length();i++){
            int s = secret.charAt(i)-'0';
            int g = guess.charAt(i)-'0';
            if(s == g)
                bulls++;
            else{
                if(numbers[s]++ < 0) cows++;
                if(numbers[g]-- > 0) cows++;
            }
        }
        return bulls + "A" + cows + "B";
    }
}
```

LEETCODE ACCEPTED : 


![Screenshot 2023-01-05 161626](https://user-images.githubusercontent.com/73281015/210764754-a98eef16-fb28-4bf7-a685-baa18c4409f7.png)














