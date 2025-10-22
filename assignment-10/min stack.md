class MinStack {
    Stack<Integer> minstk;
    Stack<Integer> stk;
    public MinStack() {
        minstk = new Stack<>();
        stk = new Stack<>();
    }
    
    public void push(int val) {
        stk.push(val);
        if(minstk.size()==0 || val<=minstk.peek()){
            minstk.push(val);
        }
    }
    
    public void pop() {
        int val = stk.pop();
        if(val==minstk.peek()){
            minstk.pop();
        }
    }
    
    public int top() {
        return stk.peek();
    }
    
    public int getMin() {
        return minstk.peek();
    }
}