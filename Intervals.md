# Intervals

+ [Merge Intervals](#merge-intervals)

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        if(intervals == null || intervals.length < 1)
            return intervals;
        
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        
        LinkedList<int[]> merged = new LinkedList<int[]>();
        
        for(int[] curr : intervals ) {
            
            if(merged.isEmpty() || merged.getLast()[1] < curr[0])
                merged.add(curr);
            
            else 
                merged.getLast()[1] = Math.max(merged.getLast()[1], curr[1]);
        }
        return merged.toArray(new int[0][]);
    }
}
```