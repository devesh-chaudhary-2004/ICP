class Solution {
    public void reorderList(ListNode head) {
        if(head.next==null) return;
        ListNode slow = head;
        ListNode fast = head.next;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode curr = slow.next;
        slow.next = null;
        ListNode prev = null;
        while(curr!=null){
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        ListNode ptr1 = head;
        ListNode ptr2 = prev;
        while(ptr1!=null && ptr2!=null){
            ListNode t1 = ptr1.next;
            ListNode t2 = ptr2.next;
            ptr1.next = ptr2;
            ptr2.next = t1;
            ptr1 = t1;
            ptr2 = t2;
        }
        
    }
}