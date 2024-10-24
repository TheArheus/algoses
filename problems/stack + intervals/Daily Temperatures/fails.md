Fail 1:
Wrong place to write a result:
```
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temps) {
        ios::sync_with_stdio(0);
        cin.tie(0);
        cout.tie(0);
        
        stack<int> tStack;
        vector<int> result(temps.size(), 0);
        for(int i = 0; i < temps.size(); i++)
        {
            while(!tStack.empty() && temps[i] > temps[tStack.top()])
            {
                result[i] = i - tStack.top();
                tStack.pop();
            }
            tStack.push(i);
        }
        return result;
    }
};
```
