class Solution {
    public String decodeString(String s) {
        Stack<Character> stk = new Stack<>();
        for(int i=0;i<s.length();i++){
            char ch = s.charAt(i);
            if(ch==']'){
                StringBuilder sb = new StringBuilder();
                while(stk.peek()!='['){
                    sb.append(stk.pop());
                }
                stk.pop();
                sb.reverse();
                StringBuilder times = new StringBuilder();
                while(stk.size()>0 && Character.isDigit(stk.peek())){
                    times.append(stk.pop());
                }
                times.reverse();
                int times2 = Integer.valueOf(times.toString());
                
                while(times2-->0){
                    for(int j=0;j<sb.length();j++){
                        stk.push(sb.charAt(j));
                    }
                }
            }
            else{
                stk.push(ch);
            }
        }
        StringBuilder ans = new StringBuilder();
        while(!stk.isEmpty()){
            ans.append(stk.pop());
        }
        return ans.reverse().toString();
    }
}