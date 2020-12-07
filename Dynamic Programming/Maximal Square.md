Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

Problem Link: <a href="https://leetcode.com/problems/maximal-square/">https://leetcode.com/problems/maximal-square/</a>
<pre>
Explanation:
	Property of a square:
	Length of row col and diagonal is same.
	
DP can only be applied if we build previously calculated solutions to build the current solution.
We need to look at 3 directions:
		      \ |
	            ___\|
find minimum in all three directions.
to check whether by adding current 1 can be extend the size of existing submatrix.  
  -> we do it by looking at the min of
     vertical length , horizontal length, diagonal length 
    We maintain a variable to keep track of largest square edge till now.

Maximal Square --> optimization
1. DP
 properties: 
 Overlapping subproblems --> 
 
 1 0 1 0 0
 1 0 1 1 1 
 1 1 1 1 1
 1 0 0 1 0

largest  --> to keep track of the largest  till now
arr[1][1] 
0 --> do nothing


Time : O(mn)
Space : O(mn) --> it can be optimised by using BINARY INDEXING
                    because we actually need only 2 rows
                    O(m) after optimization
</pre>
Solution:
<a href="https://ideone.com/SXdqmO">https://ideone.com/SXdqmO</a>
