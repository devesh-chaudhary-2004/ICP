class Pair{
    char ch ;
    int count;
    Pair(char ch,int count){
        this.ch = ch;
        this.count = count;
    }
}
class Solution {
    public String removeDuplicates(String s, int k) {
        Stack<Pair> stk = new Stack<>();
        for(int i=0;i<s.length();i++){
            char ch = s.charAt(i);
            if(stk.size()>0 && stk.peek().ch==ch){
                stk.peek().count++;
            }
            else{
                stk.push(new Pair(ch,1));
            }
            if(stk.peek().count==k){
                stk.pop();
            }
        }
        StringBuilder sb = new StringBuilder();
        while(stk.size()>0){
            Pair p = stk.pop();
            sb.append((p.ch+"").repeat(p.count));
        }
        return sb.reverse().toString();
    }
}