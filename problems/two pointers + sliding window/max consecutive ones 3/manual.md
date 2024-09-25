1004. Max Consecutive Ones III
```
#include <algorithm>
class Solution 
{
public:
    int longestOnes(vector<int>& nums, int k)
    {
        int maxLength = 0;
        int zeroCount = 0;
        int l = 0;
        int r = 0;
        while(r < nums.size())
        {
            zeroCount += !nums[r];
            while(zeroCount > k)
            {
                zeroCount -= !nums[l];
                l++;
            }

            maxLength = std::max(maxLength, r - l + 1);
            r++;
        }

        return maxLength;
    }
};
```

Description:
Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.

Examples:
Example 1:
Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
Output: 6
Explanation: [1,1,1,0,0,1,1,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

Example 2:
Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3
Output: 10
Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.
 
Constraints:
1 <= nums.length <= 105
nums[i] is either 0 or 1.
0 <= k <= nums.length
