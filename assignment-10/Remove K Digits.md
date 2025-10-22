class Solution {
    public String removeKdigits(String s, int k) {
        if(k==s.length()){
            return "0";
        }
        Stack<Character> stk = new Stack<>();
        for(int i=0;i<s.length();i++){
            while(!stk.isEmpty() && stk.peek()-'0'>s.charAt(i)-'0' && k>0){
                stk.pop();
                k--;
            }
            stk.push(s.charAt(i));
        }
        while(k>0){
            stk.pop();
            k--;
        }
        if(stk.isEmpty()){
            return "0";
        }
        String res = "";
        while(!stk.isEmpty()){
            res = res + stk.pop();
        }
        int idx = -1;
        for(int i=res.length()-1;i>=0;i--){
            if(res.charAt(i)!='0'){
                idx = i;
                break;
            }
        }
        res = res.substring(0,idx+1);
        if(res.length()==0){
            return "0";
        }
        return new StringBuilder(res).reverse().toString();
    }
}