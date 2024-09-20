Subarray Sum Equals K
```
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> prefixCount;
        prefixCount[0] = 1;
        int accumSum = 0;
        int count = 0;
        for(int num : nums)
        {
            accumSum += num;
            int prefixValue = accumSum - k;
            if(prefixCount.find(prefixValue) != prefixCount.end()){
                count += prefixCount[prefixValue];
            }
            prefixCount[accumSum]++;
        }

        return count;
    }
};
```

Description
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.
A subarray is a contiguous non-empty sequence of elements within an array.

Examples
Example 1:

Input: nums = [1,1,1], k = 2
Output: 2
Example 2:

Input: nums = [1,2,3], k = 3
Output: 2

Constraints
1 <= nums.length <= 2 * 104
-1000 <= nums[i] <= 1000
-107 <= k <= 107
