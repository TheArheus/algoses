Fails:
Fail 1:
```
#include <algorithm>
class Solution 
{
public:
    int maxDistToClosest(std::vector<int>& seats)
    {
        int result = 0;
        int l = 0;
        int r = 0;
        while(l < seats.size())
        {
			while(r + 1 < seats.size() && seats[r + 1] == seats[r]) { r++; }
			if(!seats[l])
			{
				if(l == 0) result = std::max(result, r - l + 1);
				else if(r == seats.size() - 1) result = std::max(result, r); // incorect length gathering
				else result = std::max(result, (r - l + 2) / 2);
			}
			r += 1;
			l  = r;
        }

        return result;
    }
};
```
