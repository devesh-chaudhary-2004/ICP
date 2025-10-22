class Solution {
    public int carFleet(int target, int[] position, int[] speed) {
        int n = speed.length;
        int[][] arr = new int[n][2];
        for(int i=0;i<n;i++){
            arr[i][0] = position[i];
            arr[i][1] = speed[i];
        }
        Arrays.sort(arr,(a,b)->{
            return b[0] - a[0];
        });
        int count = 0;
        double max = 0.0;
        for(int i=0;i<n;i++){
            double time = (double)(target - arr[i][0]) / arr[i][1];
            if(time > max){
                max = time; 
                count++;
            }
        }
        return count;
    }
}