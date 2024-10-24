Balanced Parantheses
```
int Solution::solve(string str)
{
    if(str.length() % 2 != 0) return 0;
    int count = 0;
    for(char c : str)
    {
        if(c == '(') count++;
        else if(c == ')') count--;
        if(count < 0) return 0;
    }
    return count == 0;
}
```

Description:
Given a string A consisting only of '(' and ')'.
You need to find whether parantheses in A is balanced or not ,if it is balanced then return 1 else return 0.

Input Format
First argument is an string A.

Output Format
Return 1 if parantheses in string are balanced else return 0.

Examples:
Example 1:
A = "(()())"
Given string is balanced so we return 1

Example 2:
A = "(()"
Given string is not balanced so we return 0

Constraints
1 <= |A| <= 105
