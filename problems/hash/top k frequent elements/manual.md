Top K Frequent elements
```
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        std::unordered_map<int, int> freqs;
        for(int num : nums)
            freqs[num]++;
        
        std::vector<std::vector<int>> num_freq(nums.size() + 1);
        for(auto [num, freq] : freqs)
        {
            num_freq[freq].push_back(num);
        }

        std::vector<int> result;
        int res_count = k;
        for(int i = num_freq.size() - 1; i >= 0; i--)
        {
            for(int j = num_freq[i].size() - 1; j >= 0; j--)
            {
                if(res_count <= 0) return result;
                result.push_back(num_freq[i][j]);
                res_count--;
            }
        }

        return result;
    }
};
```
Description:
Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

Examples:
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
Example 2:

Input: nums = [1], k = 1
Output: [1]

Constraints:
1 <= nums.length <= 105
-104 <= nums[i] <= 104
k is in the range [1, the number of unique elements in the array].
