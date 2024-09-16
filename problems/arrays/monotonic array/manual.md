Monotonic Array
```
class Solution {
public:
    bool isMonotonic(vector<int>& nums) { // [1, 2, 2, 3]
        bool is_incr = true;
        bool is_decr = false;
        for(int i = 0; i < nums.size() - 1; i++) // 0
        {
            if(is_incr && nums[i] > nums[i + 1]) is_incr = false; // true && false
            if(is_decr && nums[i] < nums[i + 1]) is_decr = false; // true && true
        }

        return is_incr || is_decr;
    }
};
```

Description:
An array is monotonic if it is either monotone increasing or monotone decreasing.

An array nums is monotone increasing if for all i <= j, nums[i] <= nums[j]. An array nums is monotone decreasing if for all i <= j, nums[i] >= nums[j].

Given an integer array nums, return true if the given array is monotonic, or false otherwise.

Examples:
Example 1:

Input: nums = [1,2,2,3]
Output: true
Example 2:

Input: nums = [6,5,4,4]
Output: true
Example 3:

Input: nums = [1,3,2]
Output: false

Constraints:
1 <= nums.length <= 105
-105 <= nums[i] <= 105
