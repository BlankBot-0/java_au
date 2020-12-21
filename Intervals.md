# Intervals

+ [Insert Interval](#insert-interval)

## Insert Interval

https://leetcode.com/problems/insert-interval/

```java
class Solution {
    
    LinkedList<int[]> merged = new LinkedList<int[]>();
    
    void mergeList(LinkedList<int[]> list, int[] interval) {
        if(list.isEmpty() || list.getLast()[1] < interval[0])
            list.add(interval);
        else
            list.getLast()[1] = Math.max(list.getLast()[1], interval[1]);
    }
    
    public int[][] insert(int[][] intervals, int[] newInterval) {
        if(intervals == null || intervals.length < 1) {
            return new int[][]{newInterval};
        }
        
        int i = 0;
        while(i < intervals.length && intervals[i][0] < newInterval[0]){
            mergeList(merged, intervals[i]);
            i++;
        }
        mergeList(merged, newInterval);
        
        while(i < intervals.length){
            mergeList(merged, intervals[i]);
            i++;
        }
        
       return merged.toArray(new int[merged.size()][]);
    }
}
```