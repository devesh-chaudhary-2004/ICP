class Solution {
    public boolean checkInclusion(String s1, String s2) {
        if(s1.length()>s2.length()) return false;
        if(s2.contains(s1)) return true;
        HashMap<Character,Integer> map1 = new HashMap<>();
        HashMap<Character,Integer> map2 = new HashMap<>();
        for(int i=0;i<s1.length();i++){
            char ch = s1.charAt(i);
            map1.put(ch,map1.getOrDefault(ch,0)+1);
        }
        for(int i=0;i<s1.length();i++){
            char ch = s2.charAt(i);
            map2.put(ch,map2.getOrDefault(ch,0)+1);
        }
        if(map1.equals(map2)) return true;
        int k = s1.length();
        for(int i=k;i<s2.length();i++){
            char prev = s2.charAt(i-k);
            char curr = s2.charAt(i);
            map2.put(prev,map2.get(prev)-1);
            if(map2.get(prev)==0){
                map2.remove(prev);
            }
            map2.put(curr,map2.getOrDefault(curr,0)+1);
            if(map1.equals(map2)) return true;
        }
        return false;

    }
}