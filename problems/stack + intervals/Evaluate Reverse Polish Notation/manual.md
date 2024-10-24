150. Evaluate Reverse Polish Notation
```
static unordered_map<string, function<int(int, int)>> opMap = 
        {
            {"+", [](int a, int b)->int{return a+b;}},
            {"-", [](int a, int b)->int{return a-b;}},
            {"*", [](int a, int b)->int{return a*b;}},
            {"/", [](int a, int b)->int{return a/b;}},
        };
        
class Solution {
    bool isNumber(const string& token)
    {
        if(token.empty()) return false;
        auto it = token.begin();
        if(*it == '-') {it++; if(it == token.end()) return false;}
        return all_of(it, token.end(), ::isdigit);
    }
public:
    int evalRPN(vector<string>& tokens)
    {
        stack<int> tStack;
        for(string token : tokens)
        {
            if(isNumber(token)) tStack.push(std::stoi(token));
            else
            {
                int b = tStack.top(); tStack.pop();
                int a = tStack.top(); tStack.pop();
                tStack.push(opMap[token](a, b));
            }
        }
        return tStack.top();
    }
};
```

Description:
You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

Note that:
The valid operators are '+', '-', '*', and '/'.
Each operand may be an integer or another expression.
The division between two integers always truncates toward zero.
There will not be any division by zero.
The input represents a valid arithmetic expression in a reverse polish notation.
The answer and all the intermediate calculations can be represented in a 32-bit integer.
 
Examples:
Example 1:
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9

Example 2:
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6

Example 3:
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
 

Constraints:
1 <= tokens.length <= 104
tokens[i] is either an operator: "+", "-", "*", or "/", or an integer in the range [-200, 200].
