81. Search in Rotated Sorted Array II
```
class Solution
{
    int findLeast(std::vector<int>& nums, int range)
    {
        int l = -1;
        int r = range - 1;
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(nums[m] > nums[range - 1])
                l = m;
            else
                r = m;
        }
        return r;
    }
public:
    bool search(std::vector<int>& nums, int target)
    {
        if(nums.size() == 1) return nums[0] == target;
        if(nums[nums.size() - 1] == target) return true;
        int r = nums.size();
        while(r - 1 > 0 && nums[0] == nums[r - 1]) r--;
        if(nums[r - 1] == target) return true;

        int newRange = r;
        int l = findLeast(nums, newRange);
            r = l + newRange;
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(nums[m % newRange] <= target)
                l = m;
            else
                r = m;
        }
        return nums[l % newRange] == target;
    }
};
```

Description:
There is an integer array nums sorted in non-decreasing order (not necessarily with distinct values).
Before being passed to your function, nums is rotated at an unknown pivot index k (0 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,4,4,5,6,6,7] might be rotated at pivot index 5 and become [4,5,6,6,7,0,1,2,4,4].

Given the array nums after the rotation and an integer target, return true if target is in nums, or false if it is not in nums.

You must decrease the overall operation steps as much as possible.

Examples:
Example 1:
Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true

Example 2:
Input: nums = [2,5,6,0,0,1,2], target = 3
Output: false
 
Constraints:
1 <= nums.length <= 5000
-104 <= nums[i] <= 104
nums is guaranteed to be rotated at some pivot.
-104 <= target <= 104
