Maximum Product of Two Elements in an Array
```
#define MAX(a, b) (a > b ? a : b)
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int max0 = 0;
		int max1 = 0;
		for(int i = 0; i < nums.size(); i++)
		{
			if(nums[i] > max1)
			{
				max0 = max1;
				max1 = nums[i];
			}
			else
			{
				max0 = MAX(max0, nums[i]);
			}
		}
		return (max0 - 1) * (max1 - 1);
    }
};
```

Description:
Given the array of integers nums, you will choose two different indices i and j of that array. Return the maximum value of (nums[i]-1)*(nums[j]-1).

Examples:
Example 1:

Input: nums = [3,4,5,2]
Output: 12 
Explanation: If you choose the indices i=1 and j=2 (indexed from 0), you will get the maximum value, that is, (nums[1]-1)*(nums[2]-1) = (4-1)*(5-1) = 3*4 = 12. 
Example 2:

Input: nums = [1,5,4,5]
Output: 16
Explanation: Choosing the indices i=1 and j=3 (indexed from 0), you will get the maximum value of (5-1)*(5-1) = 16.
Example 3:

Input: nums = [3,7]
Output: 12

Constraints:
2 <= nums.length <= 500
1 <= nums[i] <= 10^3
