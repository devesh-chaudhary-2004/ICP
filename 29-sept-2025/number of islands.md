class Solution {
    static void dfs(char[][] grid,boolean[][] vis,int i,int j,int m,int n){
        if(i<0 || i>=m || j<0 || j>=n || vis[i][j]){
            return;
        }
        vis[i][j] = true;
        int[] dr = {-1,0,1,0};
        int[] dc = {0,1,0,-1};
        for(int k=0;k<4;k++){
            int nr = dr[k] + i;
            int nc = dc[k] + j;
            if(nr>=0 && nr<m && nc>=0 && nc<n && !vis[nr][nc] && grid[nr][nc]=='1'){
                dfs(grid,vis,nr,nc,m,n);
            }
        }
    }
    public int numIslands(char[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        boolean[][] vis = new boolean[m][n];
        int count = 0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]=='1' && !vis[i][j]){
                    dfs(grid,vis,i,j,m,n);
                    count++;
                }
            }
        }
        return count;
    }
}