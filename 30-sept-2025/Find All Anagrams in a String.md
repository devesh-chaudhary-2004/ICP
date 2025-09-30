class Solution {
    public List<Integer> findAnagrams(String txt, String pat) {
        List<Integer> list = new ArrayList<>();
        if(pat.length()>txt.length()){
            return list;
        }
        HashMap<Character,Integer> map1 = new HashMap<>();
        HashMap<Character,Integer> map2 = new HashMap<>();
        for(int i=0;i<pat.length();i++){
            char ch1 = pat.charAt(i);
            char ch2 = txt.charAt(i);
            map1.put(ch1,map1.getOrDefault(ch1,0)+1);
            map2.put(ch2,map2.getOrDefault(ch2,0)+1);
        }
        if(map1.equals(map2)){
            list.add(0);
        }
        for(int i=pat.length();i<txt.length();i++){
            char ch1 = txt.charAt(i-pat.length());
            char ch2 = txt.charAt(i);
            map2.put(ch1,map2.get(ch1)-1);
            if(map2.get(ch1)==0){
                map2.remove(ch1);
            }
            map2.put(ch2,map2.getOrDefault(ch2,0)+1);
            if(map1.equals(map2)){
                list.add(i-pat.length()+1);
            }
        }
        return list;
    }
}