Given a square array of integers A, we want the minimum sum of a falling path through A.

A falling path starts at any element in the first row, and chooses one element from each row.  The next row's choice must be in a column that is different from the previous row's column by at most one.

Example 1:

Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: 12
Explanation: 
The possible falling paths are:
[1,4,7], [1,4,8], [1,5,7], [1,5,8], [1,5,9]
[2,4,7], [2,4,8], [2,5,7], [2,5,8], [2,5,9], [2,6,8], [2,6,9]
[3,5,7], [3,5,8], [3,5,9], [3,6,8], [3,6,9]
The falling path with the smallest sum is [1,4,7], so the answer is 12.

Note:
1. <= A.length == A[0].length <= 100
2. -100 <= A[i][j] <= 100

Solution
1. The array will be modified as the A. pop() is executed from the bottom to the top of the array. Each time the array is
stored as the row, the loop will be executed. Inside the loop the array is modified. The functions min, max are used to store
the minimum number immediately after the seen number. That number is added to the previous number seen. You will choose the 
minimum weight each time, then add it to the current one, and store it in A[-1][i]. The last step is to return the minimum sum in the first row.

2. In this case the sum is stored in the same square array and this give us a space complexity of O(1). An alternative could be create another square array to store the sum and return the minimum sum, but this will get a space complexity of O(n).

Note: The code can be modified to start from top-bottom or bottom-top.

3. Code
class Solution(object):
    def minFallingPathSum(self, A):
        while len(A) >= 2:
            row = A.pop()            
            for i in xrange(len(row)):
                A[-1][i] += min(row[max(0,i-1): min(len(row), i+2)])
        return min(A[0])

