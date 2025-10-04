class Solution {
    static int solve(int m,int n,int cr,int cc,int[][] dp){
            if(cr==m&&cc==n){
                return 1;
            }
            if(cr>m || cc>n){
                return 0;
            }
            if(dp[cr][cc]!=0){
                return dp[cr][cc];
            }
            int right = solve(m,n,cr,cc+1,dp);
            int down = solve(m,n,cr+1,cc,dp);
            return dp[cr][cc] = right+down;
    }
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        return solve(m-1,n-1,0,0,dp);
    }
}