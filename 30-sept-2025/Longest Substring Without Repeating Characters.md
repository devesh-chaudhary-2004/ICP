class Solution {
    public int lengthOfLongestSubstring(String st) {
        HashMap<Character,Integer> map = new HashMap<>();
        int s = 0;
        int max = 0;
        for(int i=0;i<st.length();i++){
            char ch = st.charAt(i);
            if(map.containsKey(ch)){
                if(map.get(ch)>=s){
                    s = map.get(ch)+1;
                }  
            }
            map.put(ch,i);
            max = Math.max(max,i-s+1);
        }
        return max;
    }
}