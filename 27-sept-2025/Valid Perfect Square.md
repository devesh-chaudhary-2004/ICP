class Solution {
    public boolean isPerfectSquare(int num) {
            double num2 = Math.pow(num,0.5);
            return num2 == (double)((int)num2);
    }
}