159. Longest substring with at most two distinct characters
```
#include <algorithm>
class Solution
{
public:
    int lengthOfLongestSubstringTwoDistinct(std::string s)
    {
        int maxLength = 0;
        int l = 0;
        int r = 0;
        unordered_map<char, int> charPos;
        while(r < s.length())
        {
            charPos[s[r]] = r;
            if(charPos.size() > 2)
            {
				int leftMost = s.length();
				for(const auto& [ch, pos] : charPos)
				{
					leftMost = std::min(leftMost, pos);
				}
                charPos.erase(s[leftMost]);
                l = leftMost + 1;
            }
            maxLength = std::max(maxLength, r - l + 1);
            r++;
        }
        return maxLength;
    }
};
```
