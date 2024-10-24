17. Letter Combinations of a Phone Number
```
class Solution {
public:
    vector<string> letterCombinations(string& digits) {
        array<string, 10> digitMap = 
        {
            "",
            "",
            "abc",
            "def",
            "ghi",
            "jkl",
            "mno",
            "pqrs",
            "tuv",
            "wxyz",
        };
        vector<string> result;
        function<void(string, int)> permute = [&](string curr, int i)
        {
            if(curr.length() == digits.length())
            {
                result.push_back(curr);
                return;
            }
            for(char c : digitMap[digits[i] - '0'])
                permute(curr + c, i + 1);
        };
        if(!digits.empty()) permute("", 0);
        return result;
    }
};
```
```
class Solution {
public:
    vector<string> letterCombinations(string& digits) {
        if(digits.empty()) return {};
        array<string, 10> digitMap = 
        {
            "",
            "",
            "abc",
            "def",
            "ghi",
            "jkl",
            "mno",
            "pqrs",
            "tuv",
            "wxyz",
        };
        vector<string> result;
        stack<pair<string, int>> dStack;
        dStack.push({"", 0});
        while(!dStack.empty())
        {
            auto [curr, i] = dStack.top();
            dStack.pop();

            if(curr.length() == digits.length())
            {
                result.push_back(curr);
                continue;
            }

            for(char c : digitMap[digits[i] - '0'])
                dStack.push({curr + c, i + 1});
        };
        return result;
    }
};
```

Description:
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.
A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Examples:
Example 1:
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]

Example 2:
Input: digits = ""
Output: []

Example 3:
Input: digits = "2"
Output: ["a","b","c"]
 
Constraints:
0 <= digits.length <= 4
digits[i] is a digit in the range ['2', '9'].
