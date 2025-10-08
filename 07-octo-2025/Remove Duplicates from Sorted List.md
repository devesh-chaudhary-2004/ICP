class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null || head.next==null) return head;
        ListNode curr = head.next;
        ListNode prev = head;
        while(curr.next!=null){
            if(curr.val==prev.val){
                curr = curr.next;
            }else{
                prev.next = curr;
                prev = curr;
                curr = curr.next;
            }
        }
        if(curr.val!=prev.val){
            prev.next=curr;
            prev.next.next=null;
            return head;
        }
        prev.next=null;
        return head;
    }
}