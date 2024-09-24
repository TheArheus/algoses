228. Summary Ranges
```
class Solution 
{
public:
    vector<string> summaryRanges(vector<int>& nums)
    {
        vector<string> result;
        int l = 0;
        int r = 0;
        while(l < nums.size())
        {
            while(r + 1 < nums.size() && nums[r + 1] - nums[r] == 1) r++;

            if(l != r)
                result.push_back(std::to_string(nums[l]) + "->" + std::to_string(nums[r]));
            else
                result.push_back(std::to_string(nums[l]));

            r += 1;
            l  = r;
        }

        return result;
    }
};
```

Description:
You are given a sorted unique integer array nums.

A range [a,b] is the set of all integers from a to b (inclusive).

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

"a->b" if a != b
"a" if a == b
 
Examples:
Example 1:
Input: nums = [0,1,2,4,5,7]
Output: ["0->2","4->5","7"]
Explanation: The ranges are:
[0,2] --> "0->2"
[4,5] --> "4->5"
[7,7] --> "7"

Example 2:
Input: nums = [0,2,3,4,6,8,9]
Output: ["0","2->4","6","8->9"]
Explanation: The ranges are:
[0,0] --> "0"
[2,4] --> "2->4"
[6,6] --> "6"
[8,9] --> "8->9"
 

Constraints:
0 <= nums.length <= 20
-231 <= nums[i] <= 231 - 1
All the values of nums are unique.
nums is sorted in ascending order.
