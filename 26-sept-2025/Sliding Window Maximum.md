class Solution {
   
    public int[] maxSlidingWindow(int[] nums, int k) {
        int[] ans = new int[nums.length-k+1];
        PriorityQueue<int[]> pq = new PriorityQueue<>((a,b)->{
            return b[0] -a[0];
        });
        for(int i=0;i<k;i++){
            pq.add(new int[]{nums[i],i});
        }
        ans[0] = pq.peek()[0];
        int max = ans[0];
        int i=1;
        int j=k;
        int idx = 1;
        while(j<nums.length){
           pq.add(new int[]{nums[j],j});

           while (pq.peek()[1] <= i - 1) {
                pq.poll();
            }
            ans[idx] = pq.peek()[0];
            i++;
            j++;
            idx++;
        }
        return ans;
    }
}