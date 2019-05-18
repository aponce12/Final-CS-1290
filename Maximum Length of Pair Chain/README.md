Maximum length of pair chain

You are given n pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair (c, d) can follow another pair (a, b) if and only if b < c. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order.

Example 1:
Input: [[1,2], [2,3], [3,4]]
Output: 2
Explanation: The longest chain is [1,2] -> [3,4]
Note:
The number of given pairs will be in the range [1, 1000].

1. We only need to count the longest path to the last pair. To do that we check the conditional when the pair 
b < c in the line pairs[i][1] < pairs[j][0]. If the conditional is satisfied the array dp[] is filled with the maximum number
between the last maximum value and the current one + 1. That give us the maximum number that can be created with that chain. 

2. In this case a 1D array is used to store the length of the longest chains and the maximum length is returned. 

3. Code

class Solution(object): #Time Limit Exceeded
    def findLongestChain(self, pairs):
        pairs.sort()
        dp = [1] * len(pairs)

        for j in xrange(len(pairs)):
            for i in xrange(j):
                if pairs[i][1] < pairs[j][0]:
                    dp[j] = max(dp[j], dp[i] + 1)

        return max(dp)
