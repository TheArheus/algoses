20. Valid Parentheses
```
class Solution {
public:
    bool isValid(string s)
    {
        stack<char> pStack;
        unordered_map<char, char> pMap = 
        {
            {'(', ')'},
            {'[', ']'},
            {'{', '}'}
        };
        for(char c : s)
        {
            if(pMap.count(c)) pStack.push(c);
            else
            {
                if(pStack.empty() || pMap[pStack.top()] != c) return false;
                pStack.pop();
            }
        }
        return pStack.empty();
    }
};
```

Description:
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 
Examples:
Example 1:
Input: s = "()"
Output: true

Example 2:
Input: s = "()[]{}"
Output: true

Example 3:
Input: s = "(]"
Output: false

Example 4:
Input: s = "([])"
Output: true

Constraints:
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
