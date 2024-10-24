Fail 1:
The solution is doesn't account for the max elements, that are leaving the sliding window
```
class Solution {
    stack<int> curStack;
    stack<int> maxStack;
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k)
    {
        std::vector<int> result;
        for(int i = 0; i < k; i++)
        {
            maxStack.push(maxStack.empty() ? nums[i] : std::max(maxStack.top(), nums[i]));
        }
        result.push_back(maxStack.top());
        for(int i = k; i < nums.size(); i++)
        {
            maxStack.push(std::max(maxStack.top(), nums[i]));
            result.push_back(maxStack.top());
        }
        return result;
    }
};
```
