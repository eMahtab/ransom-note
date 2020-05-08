# Ransom Note
## https://leetcode.com/problems/ransom-note

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.
```
Example 1:

Input: ransomNote = "a", magazine = "b"
Output: false

Example 2:

Input: ransomNote = "aa", magazine = "ab"
Output: false

Example 3:

Input: ransomNote = "aa", magazine = "aab"
Output: true
``` 

**Constraints: You may assume that both strings contain only lowercase letters. **



# Implementation :
```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        Map<Character,Integer> map = new HashMap<>();
        for(char ch : magazine.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        for(char ch : ransomNote.toCharArray()) {
            if(!map.containsKey(ch) || map.get(ch) == 0)
                return false;
            map.put(ch, map.get(ch) -1);
        }
        return true;
    }
}
```
