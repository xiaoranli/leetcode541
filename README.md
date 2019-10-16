# 12、leetcode344. 反转字符串II
解法一：
--  
思路：
--
    我们直接翻转每个 2k 字符块。每个块开始于 2k 的倍数，也就是 0, 2k, 4k, 6k, ...。需要注意的一件是：如果没有足够的字符，我们并不需要翻转这个块。为了翻转从 i 到 j 的字符块，我们可以交换位于 i++ 和 j-- 的字符。    
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/16 20:47
 * @descriptor
 */
public class ReverseStr_541 {
    public static String reverseStr(String s, int k) {
        if(s == null || s.length() < 2)
            return s;
        char[] chars = s.toCharArray();
        for (int i = 0; i < s.length(); i += 2*k) {
            int j = Math.min(i+k-1,s.length()-1);
            reverse(chars,i,j);
        }
        //System.out.println(Arrays.toString(chars));
        return new String(chars);
    }
    private static void reverse(char[] s,int i, int j) {
        while(i < j){
            char val = s[i];
            s[i++] = s[j];
            s[j--] = val;
        }
    }
    public static void main(String[] args) {
        String s = "abcdefg";
        String s1 = reverseStr(s, 3);
        System.out.println(s1);
    }
}
</pre>
