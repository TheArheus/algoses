1446. Consecutive Characters
```
#include <algorithm>
class Solution 
{
public:
    int maxPower(string s) 
    {
        if(s.length() == 1) return 1;

        int maxLength = 0;
        int l = 0;
        int r = 0;
        while(r < s.length())
        {
            while(r + 1 < s.length() && s[r + 1] == s[r]) r++;
            maxLength = std::max(maxLength, r - l + 1);
            r += 1;
            l  = r;
        }

        return maxLength;
    }
};
```

Description:
The power of the string is the maximum length of a non-empty substring that contains only one unique character.
Given a string s, return the power of s.

Examples:
Example 1:
Input: s = "leetcode"
Output: 2
Explanation: The substring "ee" is of length 2 with the character 'e' only.

Example 2:
Input: s = "abbcccddddeeeeedcba"
Output: 5
Explanation: The substring "eeeee" is of length 5 with the character 'e' only.
 
Constraints:
1 <= s.length <= 500
s consists of only lowercase English letters.
