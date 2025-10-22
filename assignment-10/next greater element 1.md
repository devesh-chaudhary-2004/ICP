class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        for(int i=0;i<nums1.length;i++){
            int num = nums1[i];
            boolean f = false;
            for(int j=0;j<nums2.length;j++){
                if(nums2[j]==num) {
                    f = true;
                }
                if(f && nums2[j]>num){
                    nums1[i] = nums2[j];
                    break;
                }
            }
            if(nums1[i]==num) {
                nums1[i] = -1;
            }
        }
        return nums1;
    }
}