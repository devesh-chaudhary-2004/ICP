class Solution {
    public int findMinArrowShots(int[][] points) {
        Arrays.sort(points, (a, b) -> {
        return Integer.compare(a[0], b[0]);
    
});
        int count = 1;
        int prev = points[0][1];
        for(int i=1;i<points.length;i++){
            int start = points[i][0];
            int end = points[i][1];
            if(start>prev){
                count++;
                prev = end;
            }
            prev = Math.min(prev,end);
        }
        return count;
    }
}