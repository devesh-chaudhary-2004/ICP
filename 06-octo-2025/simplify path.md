class Solution {
    public String simplifyPath(String path) {
        Stack<Character> stk = new Stack<>();
        int count = 0;
        boolean f = false;
        for(int i=0;i<path.length();i++){
            char ch = path.charAt(i);
            if(ch=='/'){
                while(stk.size()>0 && stk.peek()=='/'){
                    stk.pop();
                }
                count = 0;
                f = true;
                stk.push(ch);
            }
            else  if(ch=='.'){

                count++;
                if((i<path.length()-1 && path.charAt(i+1)=='/' && count<=2 && f) || i==path.length()-1 && count<=2 && f){
                      if(count==1){
                        if(stk.size()>1){
                            stk.pop();
                        }
                      }else{
                        for(int k=0;k<2;k++){
                            if(stk.size()>1) stk.pop();
                        }
                        while(stk.size()>1 && stk.peek()!='/'){
                            stk.pop();
                        }
                      }
                      count = 0;
                      f = false;
                      continue;
                }
                stk.push(ch);
            }else{
                f = false;
                stk.push(ch);
            }
        }
        while(stk.size()>1 && stk.peek()=='/'){
            stk.pop();
        }
       StringBuilder sb = new StringBuilder();
       if(stk.size()==0) sb.append('/');
       while(stk.size()>0){
        sb.append(stk.pop());
       }
        return sb.reverse().toString();
    }
}