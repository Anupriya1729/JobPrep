Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

Problem Link: <a href="https://leetcode.com/problems/maximal-square/">https://leetcode.com/problems/maximal-square/</a>

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
		We maintain a variable to keep track of largest sqaure till now.

Solution:

<pre>
class Solution {
    int min3(int a, int b, int c)
    {
        return min(a,min(b,c));
    }
public:
    int maximalSquare(vector<vector<char>>& arr) 
    {
        int n=arr.size(); // num of rows
        if(n==0)
            return 0;
        int m=arr[0].size(); // num of coloumns
        vector<vector<int>> dp(n,vector<int> (m,0)); // dp array
        int largest = 0; // to keep track of largest square edge
        for(int i=0;i<n;i++) 
        {
            for(int j=0;j<m;j++)
            {
                largest = max(largest,dp[i][j]);
                if(i==0 || j==0)
                {
                    dp[i][j]=arr[i][j]-'0';
                }
                else
                {
                    int v = dp[i][j-1]; // vertical length
                    int h = dp[i-1][j]; // horizontal length
                    int d = dp[i-1][j-1]; // diagonal length
                    
                    if(arr[i][j]=='1')
                    {
                        dp[i][j]=1+min3(v,h,d);
                    }
                }
                largest = max(largest,dp[i][j]);
            }
        }
        return largest*largest;
    }
};

/*
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
arr[1][2] --> 1


Time : O(mn)
Space : O(mn) --> it can be optimised by using BINARY INDEXING
                    because we actually need only 2 rows
                    O(m) after optimization

*/
</pre>
