977. Squares of a Sorted Array
```
#include <stdlib.h>
class Solution 
{
public:
    vector<int> sortedSquares(vector<int>& nums)
    {
        std::vector<int> result(nums.size(), 0);
        
        int p1 = 0;
        int p2 = nums.size() - 1;
        int i  = nums.size() - 1;
        while(p1 <= p2)
        {
            if(abs(nums[p1]) > abs(nums[p2]))
            {
                result[i] = nums[p1] * nums[p1];
                p1++;
            }
            else
            {
                result[i] = nums[p2] * nums[p2];
                p2--;
            }

            i--;
        }

        return result;
    }
};
```

Description
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Examples
Example 1:
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].

Example 2:
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 
Constraints:
1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums is sorted in non-decreasing order.
