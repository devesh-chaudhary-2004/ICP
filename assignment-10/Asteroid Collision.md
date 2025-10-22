class Solution {
    public int[] asteroidCollision(int[] arr) {
        ArrayDeque<Integer> stk = new ArrayDeque<>();
        for(int i=0;i<arr.length;i++){
            if(stk.isEmpty()){
                stk.push(arr[i]);
                continue;
            }
            if(arr[i]<0 && stk.peek()>0){
                boolean f = false;
                while(!stk.isEmpty() && stk.peek()>0){
                    if(stk.peek()<arr[i]*-1){
                        stk.pop();
                    }
                    else if(arr[i]*-1 == stk.peek()){
                        stk.pop();
                        f = true;
                        break;
                    }
                    else{
                        f = true;
                        break;
                    }
                }
                if(f==false){
                    stk.push(arr[i]);
                }
            }
            else{
                stk.push(arr[i]);
            }
            
        }
        int[] ans = new int[stk.size()];
        int idx  = ans.length-1;
        while(!stk.isEmpty()){
            ans[idx--] = stk.pop();
        }
         return ans;
    }
}