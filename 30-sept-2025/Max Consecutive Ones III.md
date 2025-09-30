class Solution {
    public int longestOnes(int[] nums, int k) {
        int i = 0;
        int j = 0;
        int maxlen = 0;
        int ones = 0;
        while(j<nums.length){
            if(nums[j]==1) ones++;
            if((j-i+1)-ones>k){
                if(nums[i]==1){
                    ones--;
                }
                i++;
            }
            
                maxlen = Math.max(maxlen,j-i+1);
            
            j++;
        }
        return maxlen;
    }
}