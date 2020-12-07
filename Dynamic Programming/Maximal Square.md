Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

Problem Link: <a href="https://leetcode.com/problems/maximal-square/">https://leetcode.com/problems/maximal-square/</a>
<pre>
Explanation:
Maximal Square --> optimization problem
DP
properties: 
Overlapping subproblems --> 
Optimal Substructure
 
Property of a square:
Length of row col and diagonal is same.
	
DP can only be applied if we use previously calculated solutions to build the current solution.
We need to look at 3 directions in our dp array:
		      \ |
	            ___\|
find minimum in all three directions.--> this is done because if any of them is zero then min will be 0 which will imply that square cannot be extended.
to check whether by adding current 1 can be extend the size of existing submatrix.  
  -> we do it by looking at the min of
     vertical length , horizontal length, diagonal length 
    
We maintain a variable to keep track of largest square edge till now.

arr                dp array
 1 0 1 0 0         1 0 1 0 0
 1 0 1 1 1    -->  1 0 1 1 1
 1 1 1 1 1         1 1 1 2 2
 1 0 0 1 0         1 0 0 1 0


largest  --> to keep track of the largest  till now
at the end largest will store 2 --> which is the edge length of square, since we need area so we return largest* largest


Time : O(mn)
Space : O(mn) --> it can be optimised by using BINARY INDEXING
                    because we actually need only 2 rows
                    O(m) after optimization
</pre>
Solution:
<a href="https://ideone.com/SXdqmO">https://ideone.com/SXdqmO</a>
