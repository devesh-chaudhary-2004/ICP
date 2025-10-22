class Solution {
    static int solver(int[] arr){
        int[] pse = new int[arr.length];
        Stack<Integer> stk = new Stack<>();
        for(int i=0;i<arr.length;i++){
            while(stk.size()>0 && arr[stk.peek()]>=arr[i]){
                stk.pop();
            }
            if(stk.size()==0){
                pse[i] = -1;
            }else{
                pse[i] = stk.peek();
            }
            stk.push(i);
        }
        int[] nse = new int[arr.length];
        stk.clear();
        for(int i=arr.length-1;i>=0;i--){
            while(stk.size()>0 && arr[stk.peek()]>=arr[i]){
                stk.pop();
            }
            if(stk.size()==0){
                nse[i] = arr.length;
            }else{
                nse[i] = stk.peek();
            }
            stk.push(i);
        }
        int maxarea = 0;
        for(int i=0;i<arr.length;i++){
           int area = arr[i] * (nse[i]-pse[i]-1);
           maxarea = Math.max(maxarea,area);
        }
        return maxarea;

    }
    public int maximalRectangle(char[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int[][] prefix = new int[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(i==0){
                    if(matrix[i][j]=='0'){
                        prefix[i][j] = 0;
                    }else{
                        prefix[i][j] = 1;
                    }
                }else{
                    if(matrix[i][j] == '0'){
                       prefix[i][j] = 0;
                    }else{
                        prefix[i][j] = prefix[i-1][j]+1;
                    }
                }
            }
        }
        int maxarea = 0;
        for(int i=0;i<prefix.length;i++){
            maxarea = Math.max(maxarea,solver(prefix[i]));
        }
        return maxarea;
    }
}