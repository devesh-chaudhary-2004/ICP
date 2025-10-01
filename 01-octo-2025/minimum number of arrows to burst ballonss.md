class Solution {
    public int findMinArrowShots(int[][] points) {
        Arrays.sort(points,(a,b)->{
             return Integer.compare(a[0],b[0]);
        });
        int end = points[0][1];
        int count = 1;
        for(int i = 1;i<points.length;i++){
            int a = points[i][0];
            int b = points[i][1];
            if(a>end){
                count++;
                end = b;
            }
            end = Math.min(end,b);
        }
        return count;
    }
}