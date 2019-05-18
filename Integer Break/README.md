Integer break

Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. 
Return the maximum product you can get.

Example 1:

Input: 2
Output: 1
Explanation: 2 = 1 + 1, 1 × 1 = 1.
Example 2:

Input: 10
Output: 36
Explanation: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.
Note: You may assume that n is not less than 2 and not larger than 58.

1. The known values of the case are stored in the first part of the array dp[]. 3*dp[i-3] satisfies the pattern that gives the maximum product 
and each calculation is stored in the array dp[i]. The last element in the array is returned as the maximum product that can be produced with
the given integer. 

2. The solution is stored in a 1D array dp[] that contains the first array case as the base case to calculate other numbers.
We will use the formula dp[n] = 3*dp[n-3] to obtain the required maximum product.

3. Code
class Solution:
    def integerBreak(self, n: int) -> int:
        case = [0,0,1,2,4,6,9]
        if n < 7:
            return case[n]
        dp = case + [0] * (n-6)
        for i in range(7, n+1):
            dp[i] = 3*dp[i-3]
        return dp[-1]
        
   
