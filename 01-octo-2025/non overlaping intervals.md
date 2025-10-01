class Solution {
    public int eraseOverlapIntervals(int[][] nums) {
        Arrays.sort(nums,(a,b)->{
            return Integer.compare(a[1],b[1]);
        });
        int prev = nums[0][1];
        int count = 0;
        for(int i=1;i<nums.length;i++){
            int start = nums[i][0];
            int end = nums[i][1];
            if(start>=prev){
                prev = end;
            }else{
                count++;
            }
        }
        return count;
    }
}