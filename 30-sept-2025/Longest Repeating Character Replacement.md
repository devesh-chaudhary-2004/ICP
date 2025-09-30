class Solution {
    public int characterReplacement(String s, int k) {
        int[] freq = new int[26];
        int maxlen = 0;
        int maxfreq = 0;
        int i=0;
        int j=0;
        while(j<s.length()){
            char ch = s.charAt(j);
            freq[ch-65]++;
            maxfreq = Math.max(maxfreq,freq[ch-65]);
            if((j-i+1)-maxfreq>k){
                freq[s.charAt(i)-65]--;
                i++;
            }
            maxlen = Math.max(maxlen,j-i+1);
            j++;
        }
        return maxlen;
    }
}