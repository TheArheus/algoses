34. Find First and Last Position of Element in Sorted Array
```
class Solution
{
    int findLeft(vector<int>& nums, int target)
    {
        int l = -1;
        int r = nums.size() - 1;
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(nums[m] < target)
                l = m;
            else
                r = m;
        }
        return nums[r] == target ? r : -1;
    }
    int findRight(vector<int>& nums, int target)
    {
        int l = 0;
        int r = nums.size();
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(nums[m] <= target)
                l = m;
            else
                r = m;
        }
        return nums[l] == target ? l : -1;
    }
public:
    vector<int> searchRange(vector<int>& nums, int target)
    {
        if(nums.empty()) return {-1, -1};
        return {findLeft(nums, target), findRight(nums, target)};
    }
};
```

Description:
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.
If target is not found in the array, return [-1, -1].
You must write an algorithm with O(log n) runtime complexity.

Examples:
Example 1:
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]

Example 2:
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]

Example 3:
Input: nums = [], target = 0
Output: [-1,-1]
 
Constraints:
0 <= nums.length <= 105
-109 <= nums[i] <= 109
nums is a non-decreasing array.
-109 <= target <= 109
