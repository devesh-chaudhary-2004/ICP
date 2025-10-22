class Solution {
    public int calculate(String s) {
        StringBuilder sb = new StringBuilder();
        List<String> list = new ArrayList<>();
        for(int i=0;i<s.length();i++){
            char ch = s.charAt(i);
            if(ch==' ')continue;
            else if(ch=='+' || ch=='-' || ch=='*' || ch=='/'){
                list.add(sb.toString());
                list.add(s.charAt(i)+"");
                sb.setLength(0);
            }else{
                sb.append(ch);
            }
        }
        list.add(sb.toString());
        Stack<String> stk = new Stack<>();
        for(int i=0;i<list.size();i++){
            if(stk.size()>0 && (stk.peek().equals("*") || stk.peek().equals("/"))){
                int b = Integer.valueOf(list.get(i));
                if(stk.peek().equals("*")){
                    stk.pop();
                    int a = Integer.valueOf(stk.pop());
                    stk.push(String.valueOf(a*b));
                }else{
                    stk.pop();
                    int a = Integer.valueOf(stk.pop());
                    stk.push(String.valueOf(a/b));
                }
            }else{
                stk.push(list.get(i));
            }
        }
        Stack<String> stk2 = new Stack<>();
        while(stk.size()>0){
            stk2.push(stk.pop());
        }
        while(stk2.size()>1){
            int a = Integer.valueOf(stk2.pop());
            String ope = stk2.pop();
            int b = Integer.valueOf(stk2.pop());
            if(ope.equals("+")){
                stk2.push(String.valueOf(a+b));
            }else{
                stk2.push(String.valueOf(a-b));
            }
        }
        return Integer.valueOf(stk2.pop());
        
    }
}