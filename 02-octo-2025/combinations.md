class Solution {
    static void solve(List<Integer> list,int num,int n,int k,List<List<Integer>> ans){
        if(list.size()==k){
            ans.add(new ArrayList<>(list));
            return;
        }
        if(num>n){
            if(list.size()==k){
            ans.add(new ArrayList<>(list));
        }
        return;
        }
        list.add(num);
        solve(list,num+1,n,k,ans);
        list.remove(list.size()-1);
        solve(list,num+1,n,k,ans);
    }
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        solve(list,1,n,k,ans);
        return ans;
    }
}