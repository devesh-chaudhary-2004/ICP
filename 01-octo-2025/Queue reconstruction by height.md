class Solution {
    public int[][] reconstructQueue(int[][] people) {
        Arrays.sort(people,(a,b)->{
            if(a[0]!=b[0]){
                   return Integer.compare(b[0],a[0]);
            }
            return Integer.compare(a[1],b[1]);
            
        });
        ArrayList<ArrayList<Integer>> ans = new ArrayList<>();
        for(int i=0;i<people.length;i++){
            int k = people[i][1];
            ArrayList<Integer> list = new ArrayList<>();
            list.add(people[i][0]);
            list.add(people[i][1]);
            ans.add(k,list); 
        }
        int[][] arr = new int[people.length][2];
        for(int i=0;i<ans.size();i++){
            arr[i][0] = ans.get(i).get(0);
            arr[i][1] = ans.get(i).get(1);
        }
        return arr;
    }
}