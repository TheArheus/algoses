Fails
Fail 1:
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
            int prefixValue = accumSum - k; // Was not the right right way
            accumSum += num;
            if(prefixCount.find(prefixValue) != prefixCount.end()){
                count += prefixCount[prefixValue];
            }
            prefixCount[accumSum]++;
        }

        return count;
    }
};
```
