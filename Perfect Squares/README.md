Perfect squares

Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

Example 1:

Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
Example 2:

Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.

1. The array is created with the last index as the integer in the input. The array is filled with the minimum number of perfect squares. 
The last integer stored in the last index is returned since it stores the least number of perfect squares that sums to that integer n. 
The line min = Math.min(min, dp[i - j*j] + 1); is the recursive line that finds the minimum number between the last number found for that 
integer and dp[i - j*j] that was calculated before + 1. As long as the while condition is satisfied, it will keep finding the minimum. 
The last min will be stored in the current index of dp[i]. Example: dp[12] = dp[12-1*1], dp[12-2*2], dp[12-3*3] = dp[11], dp[8], dp[3]. 
These values were previously calculated and stored, the minimum of all of those plus 1 is stored as the new value for dp[12]. 
2. Each sub-problem is stored in the first indexes of the array and used to calculate the next indexes until the last index is reached 
which contains the answer and is returned to the main method.
3. Code

class Solution {
    public int numSquares(int n) {
	int[] dp = new int[n + 1];
	for(int i = 1; i <= n; ++i) {
		int min = Integer.MAX_VALUE;
		int j = 1;
		while(i - j*j >= 0) {
			min = Math.min(min, dp[i - j*j] + 1);
			++j;
		}
		dp[i] = min;
	}		
	return dp[n];
    }
}
