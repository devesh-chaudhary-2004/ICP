class Solution {
    static int first(int[] nums,int target,int low,int high){
        int ans = -1;
        while(low<=high){
            int mid = low + (high-low)/2;
            if(nums[mid]==target){
               ans = mid;
               high = mid-1;
            }else if(nums[mid]>target){
                high = mid-1;
            }else{
                low = mid+1;
            }
        }
        return ans;
    }
    static int last(int[] nums,int target,int low,int high){
        int ans = -1;
        while(low<=high){
            int mid = low + (high-low)/2;
            if(nums[mid]==target){
               ans = mid;
               low = mid+1;
            }else if(nums[mid]>target){
                high = mid-1;
            }else{
                low = mid+1;
            }
        }
        return ans;
    }
    public int[] searchRange(int[] nums, int target) {
        int[] ans = {-1,-1};
        ans[0] = first(nums,target,0,nums.length-1);
        ans[1] = last(nums,target,0,nums.length-1);
        return ans;

    }
}