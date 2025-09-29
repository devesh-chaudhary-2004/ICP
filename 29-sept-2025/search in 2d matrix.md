class Solution {
    public boolean searchMatrix(int[][] mat, int target) {
        int m = mat.length;
        int n = mat[0].length;
        if(target<mat[0][0] || target>mat[m-1][n-1]) return false;
        int row = 0;
        while(row<mat.length){
            if(mat[row][n-1]==target){
                return true; 
            }
            else if(mat[row][n-1]<target){
                row++;
            }else{
                break;
            }
        }
       for(int i=0;i<n;i++){
        if(mat[row][i]==target){
            return true;
        }
       }
       return false;
    }
}