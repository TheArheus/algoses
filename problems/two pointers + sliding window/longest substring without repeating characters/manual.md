3. Longest Substring Without Repeating Characters
```
#include <algorithm>
class Solution 
{
public:
    int lengthOfLongestSubstring(string s) 
    {
        int maxLength = 0;
        int l = 0;
        int r = -1;
        unordered_map<char, int> charCounts;
        while(l < s.length())
        {
            while(r + 1 < s.length() && charCounts[s[r + 1]] == 0)
            {
                charCounts[s[r + 1]]++;
                r++;
            }
            maxLength = std::max(maxLength, r - l + 1);
            charCounts[s[l++]]--;
        }
        return maxLength;
    }
};
```

Description:
Given a string s, find the length of the longest 
substring without repeating characters.

Examples:
Example 1:
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Example 2:
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
 
Constraints:
0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.
