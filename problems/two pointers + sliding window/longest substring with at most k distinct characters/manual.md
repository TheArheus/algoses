340. Longest substring with at most K distinct characters
```
#include <algorithm>
class Solution
{
public:
    int Get(std::string s)
    {
        int maxLength = 0;
        int l = 0;
        int r = 0;
        unordered_map<char, int> charCount;
        while(r < s.length())
        {
            charCount[s[r]]++;
            while(charCount.size() > 2)
            {
                charCount[s[l]]--;
                if(charCount[s[l]] == 0) charCount.erase(s[l]);
                l++;
            }
            maxLength = std::max(maxLength, r - l + 1);
            r++;
        }
        return maxLength;
    }
};
```
