283. Move Zeroes
```
class Solution 
{
public:
    void moveZeroes(vector<int>& nums)
    {
        int p1 = 0;
        int p2 = 0;
        while(p2 < nums.size())
        {
            if(nums[p2])
            {
                nums[p1] = nums[p2];
                p1++;
            }
            p2++;
        }
        while(p1 < nums.size())
        {
            nums[p1++] = 0;
        }
    }
};
```

Description:
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.
 
Examples
Example 1:
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

Example 2:
Input: nums = [0]
Output: [0]
 
Constraints:
1 <= nums.length <= 104
-231 <= nums[i] <= 231 - 1
