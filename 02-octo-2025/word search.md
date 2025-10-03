class Solution {
    static boolean path(char[][] board, int i,int j,String word,int idx){
        if(idx==word.length()) return true;
        if(i<0 || i>=board.length || j<0 || j>=board[0].length){
            return false;
        }
        
        if(board[i][j]=='$'){
            return false;
        }
        char temp = board[i][j];
        boolean up = false;
        boolean down = false;
        boolean left = false;
        boolean right = false;
        if(temp!=word.charAt(idx)){
            return false;
        }
        board[i][j] = '$';
        up = path(board,i-1,j,word,idx+1);
        down = path(board,i+1,j,word,idx+1);
        left = path(board,i,j-1,word,idx+1);
        right = path(board,i,j+1,word,idx+1);
        
        
        board[i][j] = temp;
        return up || down || left || right;
        
    } 
    public boolean exist(char[][] board, String word) {
        int m = board.length;
        int n = board[0].length;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(board[i][j]==word.charAt(0)){
                    if(path(board,i,j,word,0)){
                        return true;
                    }
                }
            }
        }
        return false;
    }
}