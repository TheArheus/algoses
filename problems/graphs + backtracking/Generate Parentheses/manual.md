22. Generate Parentheses
```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        int total = n*2;
        vector<string> result;
        function<void(string, int)> generate = [&](string curr, int balance)
        {
#if 0
            if(balance > n || balance < 0) return;
            if(curr.length() == total && balance != 0) return;
#else
            if(balance > n - curr.length() || balance < 0) return;
#endif
            if(curr.length() == total && balance == 0)
            {
                result.push_back(curr);
                return;
            }

            generate(curr + ")", balance - 1);
            generate(curr + "(", balance + 1);
        };
        generate("(", 1);
        return result;
    }
};
```
```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        function<void(string, int, int)> generate = [&](string curr, int open, int close)
        {
            if(open + close == n*2)
            {
                result.push_back(curr);
                return;
            }
            if(open < n)
                generate(curr + '(', open + 1, close);
            if(close < open)
                generate(curr + ')', open, close + 1);
        };
        generate("", 0, 0);
        return result;
    }
};
```

Description:
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

Examples:
Example 1:
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]

Example 2:
Input: n = 1
Output: ["()"]
 
Constraints:
1 <= n <= 8
