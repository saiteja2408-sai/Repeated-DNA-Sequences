# Repeated-DNA-Sequences

import java.util.ArrayList;
import java.util.HashMap;

public class Solution {
	public List<String> findRepeatedDnaSequences(String s) {

        ArrayList<String> res = new ArrayList<String>();
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        if(s.length() < 10)
        	return res;

        int cur = 0;
        int i = 0;
        int mask = 0x7ffffff;

        while(i < 9){
        	cur = ((cur << 3) | (s.charAt(i) & 7));
        	i++;
        }

        while(i < s.length()){
        	cur = (((cur & mask) << 3) | (s.charAt(i) & 7));
        	i++;

        	if(map.get(cur) == null){
        		map.put(cur, 1);
        	}else if(map.get(cur) == 1){
        		res.add(s.substring(i - 10, i));
        		map.put(cur, 2);
        	}
        }
        return res;
    }
}
