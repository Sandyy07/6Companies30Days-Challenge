(Leetcode Problem) 
Given two positive integers left and right, find the two integers num1 and num2 such that:

left <= nums1 < nums2 <= right .
nums1 and nums2 are both prime numbers.
nums2 - nums1 is the minimum amongst all other pairs satisfying the above conditions.
Return the positive integer array ans = [nums1, nums2]. If there are multiple pairs satisfying these conditions, return the one with the minimum nums1 value or [-1, -1] if such numbers do not exist.

A number greater than 1 is called prime if it is only divisible by 1 and itself.

 

Example 1:

Input: left = 10, right = 19
Output: [11,13]
Explanation: The prime numbers between 10 and 19 are 11, 13, 17, and 19.
The closest gap between any pair is 2, which can be achieved by [11,13] or [17,19].
Since 11 is smaller than 17, we return the first pair.



CODE (JAVA) :

```
class Solution {
    public int[] closestPrimes(int left, int right) {
        List<Integer> primes = getPrimes(left,right);

        int[] ans = new int[]{0,Integer.MAX_VALUE}; 
        int m_d = ans[1]-ans[0];
        for( int i =0;i< primes.size()-1;i++){  
                int c_d = primes.get(i+1)-primes.get(i);
                if(c_d < m_d){
                    ans[0] = primes.get(i);
                    ans[1] = primes.get(i+1);
                    m_d = ans[1]-ans[0];
                }
        }
        if(m_d == Integer.MAX_VALUE) return new int[]{-1,-1};
        return ans;
    }
    public List<Integer> getPrimes(int left,int right ){
        List<Integer> primes = new ArrayList<>();
        int[] sieve = new int[1_000_001];
        Arrays.fill(sieve,1);
        for(int i = 2;i<=right;i++){
            if(sieve[i] == 1){
                if(i>=left) primes.add(i);
                for(int j=2*i ; j<=right;j+=i){
                    sieve[j]=0;
                }
            }
        }
        return primes;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-16 230816](https://user-images.githubusercontent.com/73281015/212738032-cc87ba31-8e49-4f63-8acd-7dc39e479875.png)
