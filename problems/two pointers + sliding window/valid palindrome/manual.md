125. Valid Palindrome
```
class Solution 
{
public:
    bool isPalindrome(string s) 
    {
        s.erase(std::remove_if(s.begin(), s.end(), [](char c){return !std::isalnum(c);}), s.end());
        int p1 = 0;
        int p2 = s.length() - 1;
        while(p1 < p2)
        {
            char l = std::tolower(s[p1]);
            char r = std::tolower(s[p2]);
            if(l != r) return false;
            p1++;
            p2--;
        }
        return true;
    }
};
```

Description
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
Given a string s, return true if it is a palindrome, or false otherwise.
 
Examples
Example 1:
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

Example 2:
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

Example 3:
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

Constraints:
1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.
