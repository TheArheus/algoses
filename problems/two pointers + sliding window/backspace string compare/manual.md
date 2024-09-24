844. Backspace String Compare
```
class Solution 
{
    int skipIndex(string s, int i)
    {
        int skip = 0;
        while(i >= 0)
        {
            if(s[i] == '#')
            {
                skip++;
                i--;
            }
            else if(skip > 0)
            {
                skip--;
                i--;
            }
            else break;
        }

        return i;
    }
public:
    bool backspaceCompare(string s, string t)
    {
        int p1 = s.length();
        int p2 = t.length();
        while(p1 >= 0 && p2 >= 0)
        {
            p1 = skipIndex(s, p1 - 1);
            p2 = skipIndex(t, p2 - 1);

            if(p1 < 0 && p2 < 0) return true;
            if(p1 < 0 || p2 < 0 || s[p1] != t[p2]) return false;
        }

        return true;
    }
};
```

Description:
Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

Examples:
Example 1:
Input: s = "ab#c", t = "ad#c"
Output: true
Explanation: Both s and t become "ac".

Example 2:
Input: s = "ab##", t = "c#d#"
Output: true
Explanation: Both s and t become "".

Example 3:
Input: s = "a#c", t = "b"
Output: false
Explanation: s becomes "c" while t becomes "b".
 
Constraints:
1 <= s.length, t.length <= 200
s and t only contain lowercase letters and '#' characters.
