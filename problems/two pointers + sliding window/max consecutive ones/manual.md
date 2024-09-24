485. Max Consecutive Ones
```
#include <algorithm>
class Solution 
{
public:
    int findMaxConsecutiveOnes(vector<int>& nums) // [1,1,0,1,1,1]
    {
        int result = 0;
        int l = 0;
        int r = 2;
        while(l < nums.size())
        {
            while(r + 1 < nums.size() && nums[r + 1] == nums[r]) r++; // true, true, false
            result = std::max(result, r - l + 1);
            r += 1;
            l  = r;
        }

        return result;
    }
};
```

Description:
Given a binary array nums, return the maximum number of consecutive 1's in the array.

Examples:
Example 1:
Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.

Example 2:
Input: nums = [1,0,1,1,0,1]
Output: 2
 
Constraints:
1 <= nums.length <= 105
nums[i] is either 0 or 1.
