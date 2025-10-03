class Solution {
    static void solve(List<Integer> list,int idx,int[] arr,int target,ArrayList<List<Integer>> ans){
        if(target==0){
            ans.add(new ArrayList<>(list));
            return;
        }
        if(idx>=arr.length || target<0){
            return;
        }
        list.add(arr[idx]);
        solve(list,idx+1,arr,target-arr[idx],ans);
        list.remove(list.size()-1);
        int next = idx + 1;
        while (next < arr.length && arr[next] == arr[idx]) {
            next++;
        }
        solve(list,next,arr,target,ans);
    }
    public List<List<Integer>> combinationSum2(int[] arr, int target) {
        ArrayList<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        Arrays.sort(arr);
        solve(list,0,arr,target,ans);
        return ans;
    }
}