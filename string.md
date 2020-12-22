# String

+ [Group Anagrams](#group-anagrams)

## Group Anagrams

https://leetcode.com/problems/group-anagrams/

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> groups = new HashMap<String, List<String>>();
        
        for (String word : strs) {
            char[] chars = word.toCharArray();
            Arrays.sort(chars);
            String group = Arrays.toString(chars);
            if (!groups.containsKey(group)) groups.put(group, new ArrayList<>());
            groups.get(group).add(word);
        }
        
        return new ArrayList<>(groups.values());
    }
}
```