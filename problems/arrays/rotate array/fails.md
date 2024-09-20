Fails
Fail 1(not really the correct solution):

```
#include <algorithm>
class Solution {
public:
    void rotate(vector<int>& nums, int k)
    {
        if(!nums.size() || nums.size() == 1 || k == 0 || nums.size() == k) return;

        k = k % nums.size();
        int p1 = 0;
        int p2 = nums.size() - k;
        while(p1 < k)
        {
			std::swap(nums[p1], nums[p2]);
            p1++;
            p2++;
        }

        if(nums.size() % 2 == 0) return;
		while(p1 < nums.size() - 1)
		{
			p2 = p1 + 1;
			std::swap(nums[p1], nums[p2]);
			p1++;
		}
    }
};
```
