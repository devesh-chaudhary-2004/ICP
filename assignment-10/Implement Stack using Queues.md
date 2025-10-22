class MyStack {
       Queue<Integer> q1 ;
        Queue<Integer> q2 ;
    public MyStack() {
        q1 = new LinkedList<>();
        q2 = new LinkedList<>();
    }
    
    public void push(int x) {
        q1.add(x);
    }
    
    public int pop() {
        while(q1.size()>1){
           q2.add(q1.poll());
        }
        int num = q1.poll();
        while(!q2.isEmpty()){
             q1.add(q2.poll());
        }
        return num;
    }
    
    public int top() {
        while(q1.size()>1){
           q2.add(q1.poll());
        }
        int num = q1.peek();
        q2.add(q1.poll());
        while(!q2.isEmpty()){
             q1.add(q2.poll());
        }
        return num;
    }
    
    public boolean empty() {
        if(q1.size()==0){
            return true;
        }
        return false;
    }
}